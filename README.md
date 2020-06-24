# Swifty Words

## Installing

```
git alone
```

## Features

### loadView()

loadView() is a method to be called by the viewController.  This method is invoked when the current view is nil and want to create the UI elements programmatically.  It's to be employed when you're not creating the UI elements in the storyboard.  In fact, if you're using the Interface Building to create your UI elements, this method is not be overridden, but the viewDidLoad() method to be used, instead.

### Anchors

```
NSLayoutConstraint.activate([
    scoreLabel.topAnchor.constraint(equalTo: view.layoutMarginsGuide.topAnchor),
    scoreLabel.trailingAnchor.constraint(equalTo: view.layoutMarginsGuide.trailingAnchor),
    cluesLabel.topAnchor.constraint(equalTo: scoreLabel.bottomAnchor),
    cluesLabel.leadingAnchor.constraint(equalTo: view.layoutMarginsGuide.leadingAnchor, constant: 100),
    cluesLabel.widthAnchor.constraint(equalTo: view.layoutMarginsGuide.widthAnchor, multiplier: 0.6, constant: -100),
    answersLabel.topAnchor.constraint(equalTo: scoreLabel.bottomAnchor),
    answersLabel.trailingAnchor.constraint(equalTo: view.layoutMarginsGuide.trailingAnchor, constant: -100),
    answersLabel.widthAnchor.constraint(equalTo: view.layoutMarginsGuide.widthAnchor, multiplier: 0.40, constant: -100),
    answersLabel.heightAnchor.constraint(equalTo: cluesLabel.heightAnchor),
    currentAnswer.centerXAnchor.constraint(equalTo: view.centerXAnchor),
    currentAnswer.widthAnchor.constraint(equalTo: view.widthAnchor, multiplier: 0.50),
    currentAnswer.topAnchor.constraint(equalTo: cluesLabel.bottomAnchor, constant: 20),
    submit.topAnchor.constraint(equalTo: currentAnswer.bottomAnchor),
    submit.centerXAnchor.constraint(equalTo: view.centerXAnchor, constant: -100),
    submit.heightAnchor.constraint(equalToConstant: 44),
    clear.centerXAnchor.constraint(equalTo: view.centerXAnchor, constant: 100),
    clear.centerYAnchor.constraint(equalTo: submit.centerYAnchor),
    clear.heightAnchor.constraint(equalToConstant: 44),
    buttonsView.widthAnchor.constraint(equalToConstant: 750),
    buttonsView.heightAnchor.constraint(equalToConstant: 320),
    buttonsView.centerXAnchor.constraint(equalTo: view.centerXAnchor),
    buttonsView.topAnchor.constraint(equalTo: submit.bottomAnchor, constant: 200),
    buttonsView.bottomAnchor.constraint(equalTo: view.layoutMarginsGuide.bottomAnchor, constant: -20),
])
```

### Priority

- Content hugging priority determines how likely this view is to be made larger than its intrinsic content size. If this priority is high it means Auto Layout prefers not to stretch it; if it’s low, it will be more likely to be stretched.
- Content compression resistance priority determines how happy we are for this view to be made smaller than its intrinsic content size.

1.png

```
cluesLabel.setContentHuggingPriority(UILayoutPriority(1), for: .vertical)
answersLabel.setContentHuggingPriority(UILayoutPriority(1), for: .vertical)
```

2.png
