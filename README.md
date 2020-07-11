# Swifty Words

An iOS app to demonstrate the programmatic ways of Auto Layout, including NSLayoutConstraint and NSLayoutAnchor.

## Features

### loadView()

loadView() is a method to be called by the viewController.  This method is invoked when the current view is nil and want to create the UI elements programmatically.  It's to be employed when you're not creating the UI elements in the storyboard.  In fact, if you're using the Interface Building to create your UI elements, this method is not be overridden, but the viewDidLoad() method to be used, instead.

### Layout Constraints

Three ways of defining the Auto Layout constraints:
1. Using the Interface Builder:

Interface Builder has a number of ways to construct the Auto Layout constraints. It includes using the suggested constraints, adding individual constraints manually or using the Horizontal/Vertical Stack Views. 

2. Using NSLayoutConstraint:
This is the most verbose way of applying constraints. 

```
NSLayoutConstraint(item: subview,
                   attribute: .leading,
                   relatedBy: .equal,
                   toItem: view,
                   attribute: .leadingMargin,
                   multiplier: 1.0,
                   constant: 0.0).isActive = true
```

3. Using NSLayoutAnchor:

There are two ways of applying NSLayoutAnchor. The first is by setting the isActive property to true:
```
subview.leadingAnchor.constraint(equalTo: margins.leadingAnchor).isActive = true
```
This methods makes toggling the constraint on and off dynamically easy.

Second is to use the the NSLayoutConstraint’s activate API:
```
let constraint = subview.leadingAnchor.constraint(equalTo: margins.leadingAnchor)
NSLayoutConstraint.activate([constraint])
```

If we were to apply the constraints programmatically, it’s important to set the translatesAutoresizingMaskIntoConstraints
 property to false.  translatesAutoresizingMaskIntoConstraints is a Boolean value that determines whether the view’s autoresizing mask gets translated to Auto Layout constraints. 

### Priority

- Content hugging priority determines how likely this view is to be made larger than its intrinsic content size. If this priority is high it means Auto Layout prefers not to stretch it; if it’s low, it will be more likely to be stretched.
- Content compression resistance priority determines how happy we are for this view to be made smaller than its intrinsic content size.

```
cluesLabel.setContentHuggingPriority(UILayoutPriority(1), for: .vertical)
answersLabel.setContentHuggingPriority(UILayoutPriority(1), for: .vertical)
```


