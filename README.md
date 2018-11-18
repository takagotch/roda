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

```
```


