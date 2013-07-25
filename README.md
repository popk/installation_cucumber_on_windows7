# มาสร้างบ้านให้กับเจ้าหนูน้ำ (Capybara) กันเถอะ!!

หลังจากที่เราลง Environment ต่างๆที่จำเป็นกันจบครบแล้ว ขั้นตอนต่อไป จะเป็นการสร้างบ้านให้กับเจ้า capybara.

อันดับแรก ให้สร้าง Folder เอาชื่อตามงานที่ทำ หรือเอาที่ชอบๆละกัน เช่น capybara เลยเล่นง่ายดีฮะ :D.

```
C:\>mkdir capybara
```

หลังจากนั้นให้เข้าไปในตัวเจ้า capybara และสร้าง folder บังคับ เริ่มต้นด้วย features

```
C:\capybara>mkdir features
```

เข้าไปใน features สร้างอีก 2 folder ที่จำเป็น

```
C:\capybara\features>mkdir support
และ
C:\capybara\features>mkdir steps
```

หลังจากนั้นก็สร้างไฟล์ที่ชื่อ Gemfile(เป็นไฟล์ไม่ต้องมีนามสกุล) เก็บไว้ใน path C:\capybara>

```gem
source 'https://rubygems.org'

gem 'cucumber-rails', '0.3.2'  #Necessary and Compatible for IE Browser
gem 'capybara', '0.4.0.rc'     #Necessary and Compatible for IE Browser
```

จากนั้น run คำสัง bundle install ไปก่อน 1 ทีเพื่อเรียกใช้ bundle ต่างๆที่จำเป็น

```
C:\capybara>bundle install
```

เรียบร้อยแล้ว อันดับต่อไป สร้างไฟล์ env.rb ที่ path C:\capybara\features\support

```ruby
require 'capybara/cucumber'
require 'selenium-webdriver'  #require for ie browser
require 'rubygems'				    #require for ie browser
require 'rspec/expectations'	#require for ie browser

Capybara.app = "www.google.com" #you can change this default domain
Capybara.app_host = 'www.google.com'  #you can change this default domain
Capybara.default_selector = :css
Capybara.default_driver = :selenium
Capybara.register_driver :selenium do |app|			#require for ie browser
  Capybara::Selenium::Driver.new(app, :browser => :internet_explorer )
end
```
