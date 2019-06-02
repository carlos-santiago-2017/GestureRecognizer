# GestureRecognizer

# Chapter 17 Taps, Touches, and Gestures

# Multitouch Terminology

- A gesture is passed through the system inside a series of events.
- Events are generated when you interact with the device´s multitouch screen. They contain information about the touch or touches that ocurreed
- Touch refers to a finger being placed on the screen.
- Tap happens when you touch the screen with the finger and then inmediatelly lift your finger off the screen without moving it around.
- A gesture recognizer is an object that knows how to watch the stream of events generated by a user and recognize when the user is touching and dragging in a way that matches a predefined gesture.

# The Responder Chain

# Responding to Events

# Forwarding and Event: Keeping the responder chain alive.

``` objective-c
- (void)respondToFictionalEvent:(UIEvent *)event
{   
    if([self shouldHandleEvent:event])
    {
        [self handleEvent:event];
    }
    else 
    {
        [[self nextResponder] respondToFictionalEvent: event];
    }
}
```

# The Multitouch Architecture

# The Four Touch Notification Methods

``` objective-c
- (void)touchesBegan:(NSSet *)touches withEvent:(UIEvent *)event
{
    NSUInteger numTaps = [[touches anyObject] tapCount];
    NSUInteger numTouches = [touches count];
    // Do something here.
}
```


# Another 

A gesture recognizer is an object that will listen for the user to input a common gesture and will call an action when the particular gesture is recognized.

A gesture is tied to a single view, but a view can have multiple gestures.

# Programmatic Actions

Interface Builder connects controls to actions

In order to connect a button to a method programmatically, you will need a reference to the button in code. Use Interface Builder to create an IBOutlet to any methods

``` swift
@IBOutlet weak var button: UIButton!
```

``` swift
//
//  ViewController.swift
//  GestureRecognizer
//
//  Created by Carlos Santiago Cruz on 23/08/18.
//  Copyright © 2018 Carlos Santiago Cruz. All rights reserved.
//

import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
    }
    @IBAction func tapGestureOcurred(_ sender: UITapGestureRecognizer) {
        let location = sender.location(in: view)
        print(location)
        // it prints the coordinates where you tapped on screen. Look at the console
        // no necesita de un outlet, preguntar por qué ?

    }
    

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }


}
```

