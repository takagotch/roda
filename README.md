### roda
---
https://github.com/jeremyevans/roda

```
gem install roda
```

```ruby
# config.ru
require "roda"
class App < Roda
  route do |r|
    # GET / request
    r.root do
      r.redirect "/hello"
    end
    # /hello branch
    r.on "hello" do
      @greeting = 'Hello'
      # GET /hello/world request
      r.get "world" do
        "#{@greeting} world!"
      end
      # /hello request
      r.is do
        # GET /hello request
        r.get do
          "#{@greeting}"
        end
        # POST /hello request
        r.post do
          puts "Someone said #{@greeting}"
          r.redirect
        end
      end
    end
  end
end
run App.freeze.app

r.on "" do
end

r.get do
end

r.post do
end

r.on "" do
end

class App < Roda
end



```

```rb
class App < Roda
  plugin :hash_routes
  
  hash_branch "api" do |r|
  end
  
  route do |r|
    r.hash_routes
  end
end

run App.app

Roda.opts[:layout] = "guest"

class Users < Roda; end
class Admin < Roda
  opts[:layout] = "admin"
end

Users.opts[:layout]
Admin.opts[:layout]


class App < Roda
  plugin :render
  
  route do |r|
    render("home", locals: {content: "hello, world"})
  end
  
  r.get "" do
    @var2 = '1'
    
    view("home")
  end
end

class App < Roda
  plugin :render,
    excape: true,
    views: 'admin_views',
    layout_opts: {template: 'admin_layout', engine: 'html.erb'},
    template_opts: {default_encoding: 'UTF-8'}
end

require 'roda'
class App < Roda
  plugin :sessions, secret: ENV['SESSION_SECRET']
end

require 'roda'
require 'roda/session_middleware'
class App < Roda
  use RodaSessionMiddleware, secret: ENV['SESSION_SECRET']
end

route do |r|
  r.public
  r.assets
  
  check_csrf!
end

request.params['foo_id'].to_i

some_method(request.params['bar'])

class App < Roda
  plugin :content_security_policy do |csp|
    csp.default_src :none
    csp.script_src :self
    csp.connect_src :self
    csp.img_src :self
    csp.font_src :self
    csp.form_action :self
    csp.base_uri :none
    csp.frame_ancestors :none
    csp.block_all_mixed_content
    csp.report_uri 'CSP_REPORT_URI'
  end
end


class Roda
  module RodaPlugins
    module Markdown
      module InstanceMethods
        def markdown(str)
          BlueCloth.new(str).to_html
        end
      end
    end
    
    register_plugin :markdown, Markdown
  end
end


module MarkdownHelper
  module InstanceMethods
    def markdown(str)
      BlueCloth.new(str).to_html
    end
  end
end

Roda.plugin MarkdownHelper

class App < Roda
  plugin :default_headers,
    'Content-Type'=>'text/html',
    'Strict-Transport-Security'=>'max-age=16070400',
    'X-Content-Type-Options'=>'nosniff',
    'X-Frame-Options'=>'deny',
    'X-XSS-Protection'=>'1; mode=block'
end
```
