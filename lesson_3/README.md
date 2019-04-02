# Lesson 3 - Gaze Based Interaction

In this lesson, you'll create your own project and implement triggering events based on where you're looking. 


# Create Project

Sign in at https://glitch.com/ and then click New Project in the top right corner. Choose hello-webpage to start your project. 

Replace the code in the html with the code below

```html
<html>
  <head>
    <!-- Scripts, link to CSS files go here  -->
  </head>
  <body>
    <!-- Code that puts objects in your scene go here -->
  </body>
</html>
```

# Add Scripts

In order to make A-frame available to your webpage, you need to add a script in between the head tags. 

`<script src="https://aframe.io/releases/0.9.0/aframe.min.js"></script>`

We also need to make available the events that will trigger our interactions. So put this code in between your head tags. 

`<script src="https://unpkg.com/aframe-event-set-component@4.2.1/dist/aframe-event-set-component.min.js"></script>
`

Your index.html should look like this 

```html
<html>
  <head>
    <script src="https://aframe.io/releases/0.9.0/aframe.min.js"></script>
    <script src="https://unpkg.com/aframe-event-set-component@4.2.1/dist/aframe-event-set-component.min.js"></script>
  </head>
  <body>
    <!-- Code that puts objects in your scene go here -->
  </body>
</html>
```

# Add Camera and Cursor

First, let's add a camera to the scene so we know where we are looking

Put this in the body of your index.html

```html
<a-scene>
  <a-camera>
    <a-cursor></a-cursor>
  </a-camera>
</a-scene> 
```

When you open your app, you should see a small black circle. This is the pointer that tracks your gaze.

Now let's add a couple of boxes that we can interact with. 

# Add boxes

So we're going to use the [event-system](https://github.com/aframevr/aframe/blob/master/docs/introduction/interactions-and-controllers.md#gaze-based-interactions-with-cursor-component) in A-frame to handle interactions. 

It's a little complicated but you can essentially break it down into three parts: the name of the event, the type of the event, and what is the event changing. 

Let's look at an example. Add this to the body in your index.html

```html
<a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"
       event-set__enter="_event: mouseenter; color: #8FF7FF"
       event-set__leave="_event: mouseleave; color: #4CC3D9">
</a-box>
```

We have two events here: enter and leave. This name can be anything you want but it should probably be related to the event type. 

Then we have two event types: `mouseenter` and `mouseleave`. We also have `click`, `mousedown`, and `mouseup` as event types. 

Finally, we have what we are changing here, the color. The color will become lighter when the cursor enters the object and reset the color when the cursor leaves the object(the reason it's called mouseenter even though the mouse is not going to be the main input is to make it similar to traditional web development code).

## Alternative 

There is an alternative way to define events that only has two parts: the event type and what's being changed. Let's take a look at an example. Add this to the body of your html. 

```html
<a-box position="-3 0.5 -3" color="green"
       event-set__click="color: red; scale: 2 2 2"
       event-set__mouseenter="color: blue">
</a-box>
```

As you can see, we define the event type right in the event id and then we just define what is being changed. We also see how we can change multiple properties with one event. We separate the different properties with a semi-colon.

You can pick either one. The three-part way has been around for longer so most likely a lot of resources (e.g. tutorials, documentation) will use that way. 

## Challenge

Go back into one of your scenes and now add some interaction. 

1. Add the camera and cursor
2. Add a click event with one of your primitives
3. Add a mouseenter, mouseleave event with one of your primitives

One of your events should modify multiple properties. 




