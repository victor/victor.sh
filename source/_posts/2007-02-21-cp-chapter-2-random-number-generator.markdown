---
layout: post
title: "CP, Chapter 2: Random number generator"
---

After telling XCode which name we want to give to the project, it will generate its skeleton. As we can see, an `rb_main.rb` script has been created, that is called from the entry point (in `main.m`); and the RubyCocoa framework has been added as well. If we build and launch this project, we can see that it runs normally.

![Project files](http://principia.info/assets/2007/2/17/CP_2_2_XCode_RbRandomApp.png)

If we look closely at the generated code, we'll see that `main.m`, instead of calling `NSApplicationMain`, is actually calling `RbApplicationMain` and passing it the script name as an argument.

The script, for its part, looks somewhat more complex:



    require 'osx/cocoa'

    def rb_main_init
      path = OSX::NSBundle.mainBundle.resourcePath.fileSystemRepresentation
      rbfiles = Dir.entries(path).select {|x| /\.rb\z/ =~ x}
      rbfiles -= [ File.basename(__FILE__) ]
      rbfiles.each do |path|
        require( File.basename(path) )
      end
    end

    if $0 == __FILE__ then
      rb_main_init
      OSX.NSApplicationMain(0, nil)
    end

The first thing the script does is require the Cocoa libraries (for Ruby). Then defines a function, `rb_main_init`, that is called if the script it's the same as the one that was passed as a parameter, proceeding then to call the method `NSApplicationMain`, which loads the NIB files and begins the main Cocoa application loop.

What does this function do? It iterates over the package (the bundle) files, looking for all the ruby scripts within, and `require` them all, presumably so that they are available before being used from the application.

Having seen this, we can proceed with the application, launching Interface Builder and defining the interface, as explained in the book. Once the main application window is created, we are expected to define a class `Foo` with an outlet and an action, and then have XCode generate the code for that class. But XCode does not yet generate Ruby code, so the only thing we can obtain from it is Objective-C code. I have done this in order to convert it to Ruby, but you can skip this step and use the following code:


    #
    #  Foo.rb
    #  RbRandomApp
    #
    #  Created by Victor Jalencas on 18/02/07.
    #

    require 'osx/cocoa'

    class Foo < OSX::NSObject

    	ib_outlets :textField
	
    	def generate(sender)
    	end
	
    	def seed(sender)
    	end

    end


Now we're ready to instantiate Foo. If we look at the Connection inspector, we'll see that there is an outlet, which is there thanks to the class method we used to declare it, `ib_outlets` (which is, actually, an alias to `attr_writer`). However, there isn't yet a method for declaring the actions, so that our only course of action is adding them by hand in Interface Builder. I've heard rumors that it will soon exist such a method, though.

Next, we'll connect the outlets and actions as normally. Then it's just a matter of implementing the methods we had declared:


    #
    #  Foo.rb
    #  RbRandomApp
    #
    #  Created by Victor Jalencas on 18/02/07.
    #

    require 'osx/cocoa'

    class Foo < OSX::NSObject

    	ib_outlets :textField
	
    	def generate(sender)
    	  generated = (rand(100))+1
    	  @textField.setIntValue(generated)
    	end
	
    	def seed(sender)
    	  srand(Time.now.to_i)
    	  @textField.setStringValue "Generator seeded"
    	end

    end

If we build and launch the project now, we'll see that it works perfectly. Where in the original code we would have called C functions (`random`, `srand` and `time`), I have now used the ruby counterparts.
We'll also see that the outlets are used as instance variables, and that there's no need to convert ruby strings to `NSString` (that is one of the few automatic conversions RubyCocoa offers us)

To finish the example, we'll add the `awakeFromNib` method:


	def awakeFromNib
	  now = OSX::NSCalendarDate.calendarDate
	  @textField.setObjectValue now
	end

And with this, the application is finished. We could run the Ruby and the ObjC applications side-by-side and we'd get the same results, save for the fact that in Ruby, if you don't seed the random number generator, it's by default seeded with a value that depends on the time and the PID, while the C function `random` does not and will always repeat the same sequences if it's not properly seeded.
