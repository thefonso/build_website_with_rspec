# This is a simple 'RSpec in Rails' website Kata
It will show how to make simple form,
Create links to other pages and
It will also show how to write basic tests TDD style.

"Fork" this code to begin.

Then add this to your gemfile and run bundle install

    group :development do
      gem "rspec-rails", ">= 2.10.0" 
      # gem "webrat", ">= 0.7.2" 
    end


Simple company website:
 
    I want a company logo
    I want a picture of the company building
    I want text describing how awesome the company is
    I want a simple website  (home, contact us,  about us)
    I want a contact form for my visitors
    The form should have a name, email, and comments field


Becomes

    it should display a company logo on each page
    it should show a picture of the company building on the front page
    it "should display text about the company on the front page"
    it "should have three pages, home, about, contact"
    it "should have a name, email and comments field"
    
    
Part2 - Create a pending block We will begin our journey with our first "describe" block.

    Our first describe block:

    describe "simple company website" do
        it should display a company logo on each page
        it should show a picture of the company building on the front page
        it "should display text about the company on the front page"
        it "should have three pages, home, about, contact"
        it "should have a name,email and comments field"
    end
    
    
Part3 - We can split our "it should do" statements up like so...

    describe "simple company website" do
        it "should display a company logo on each page" do
         "verify an element exist on each page named logo.jpg"
        end

        it "should show a picture of the company building on the front page" do
         "verify an element exist on the front page named building.jpg"
        end

        it "should display text about the company on the front page" do
         "verify a paragraph with id="description of company" text is on front page"
        end

        it "should have three pages home, about, contact" do
         "code here verifies presence of pages"
        end

        it "should have a name,email and comments field" do
         "code here verifies presence of each field"
        end
    end
    
Part4 - Replace the Pending code with working code

Now we will begin building our app starting with thinking about each test in our app...making a failing test (red)...making it pass (green) and so on until each test passes...after which we will have a self documenting app that will be a LOT more easily maintained over the course of it's lifetime.


#Resources:

See the git cheat sheet in this repo.

    https://github.com/thefonso/class_website/blob/master/git_cheat_sheet.md



Also it's suggested that you keep the RSpec documentation on hand in a browser tab.

    http://rubydoc.info/gems/rspec-expectations

    http://rubydoc.info/gems/rspec-mocks/#Setting_Responses

    http://rubydoc.info/gems/rspec-core/#nested_groups



