---
layout: post
title: "Integrating openid, google apps, and ruby on rails"
date: 2010-05-28 19:40
comments: false
categories: 
alias: [journal/2010/5/28/integrating-openid-google-apps-and-ruby-on-rails.html]
---
                                                                 
My university uses Google Apps for Universities. We wanted users to be able to authenticate to our rails application using their Google Apps account. Since Google Apps now supports openid, I thought that this would be really straightforward. A friend had just installed openid on his site and it was a breeze. I thought I would just install a few gems and get on with other rails development activities. I have no intention of becoming an openid expert. Here are the steps that I followed to get it to all work together.

 

Step 1) Enable Federated Login using OpenID on your Google Apps domain.

http://www.google.com/a/cpanel/{your-domain}/SetupIdp

Step 2) Download your needed gems

a) gem install ruby-openid
This is JanRan's ruby implementation of open id

b) gem install ruby-openid-apps-discovery
This is Google's extension of ruby-openid to work with Google Apps

c) gem install rack-openid
This is a rack wrapper around JanRan's open id

d) ./script/plugin install git://github.com/rails/open_id_authentication.git
This is Rails code to make integrating in with open id easier

e) Modify config/environment.erb and add this line
require 'gapps_openid'

Step 3) Add some code to your rails application.

 
```ruby
 
class SessionsController < current_user =" @account.users.authenticate(params[:name]," required =""> ["http://axschema.org/contact/email", "http://axschema.org/namePerson/first", "http://axschema.org/namePerson/last"]) do |result, identity_url, registration|
       ax_response = OpenID::AX::FetchResponse.from_success_response(request.env[Rack::OpenID::RESPONSE])
         case result.status
         when :missing
           failed_login "Sorry, the OpenID server couldn't be found"
         when :invalid
           failed_login "Sorry, but this does not appear to be a valid OpenID"
         when :canceled
           failed_login "OpenID verification was canceled"
         when :failed
           failed_login "Sorry, the OpenID verification failed"
         when :successful
 

       email = ax_response['http://axschema.org/contact/email'].first()
       first_name = ax_response['http://axschema.org/namePerson/first'].first()
       last_name = ax_response['http://axschema.org/namePerson/last'].first()

       if result.successful?
         #Look up the user and if they don't exist then create the user
         @current_user = ...
         if @current_user
           successful_login
         else
           failed_login "Sorry, no user by that identity URL exists (#{identity_url})"
         end
       else
         failed_login result.message
       end
     end
   end
 end

   private
     def successful_login
       session[:user_id] = @current_user.id
       redirect_to(root_url)
     end

     def failed_login(message)
       flash[:error] = message
       redirect_to(new_session_url)
     end
 end

```

 

 

If you are still stuck, here are some other helpful links:

To understand open id: http://www.devx.com/opensource/Article/37692/1954?pf=true

To get google mail to work with rails plugin: http://stackoverflow.com/questions/2492043/ruby-open-id-authentication-with-google-openid

To understand all possible AX schema fields: http://www.axschema.org/types/#sreg

Discovering end points: http://groups.google.com/group/google-federated-login-api/web/openid-discovery-for-hosted-domains

 

Part 2


If you get a warning message like this
WARNING: making https request to https://www.google.com/accounts/o8/.well-known/host-meta?hd= without verifying server certificate; no CA path was specified.
WARNING: making https request to https://www.google.com/accounts/o8/site-xrds?ns=2&hd= without verifying server certificate; no CA path was specified.
WARNING: making https request to https://www.google.com/a//o8/ud?be=o8 without verifying server certificate; no CA path was specified.
Generated checkid_setup request to https://www.google.com/a//o8/ud?be=o8 with assocication AOQpcUfj9hGDs4DukDUrxhChnVBMbtoKAlXgvzQ1dp1L0yp6wCDxeFlx

 

The fix is pretty simple.
a) In your config/environment.rb file add the line
OpenID.fetcher.ca_file = "#{Rails.root}/config/ca-bundle.crt"
b) You'll need to get a ca-bundle.crt file. You should add in certificate authorities that you trust. If you are in a hurry, you can use the one in the ruby-openid-apps-discovery gem. Unpack it and find it in the lib directory. I copied mine to my application's config directory.
