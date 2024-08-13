# tween-cpp

Simple header-only tweening library written in C++

Tween objects can be made for any type meeting the following:
 - Addition and subtraction operators defined with itself
 - Multiplication operator defined for floats

Example code for tweening floats:
```cpp
Tween<float> tweener;

float value = 5.0f;
float secondValue = 7.0f;

// Tween value from 5 to 10, taking 3 seconds
// with elastic transition and ease in-out easing
tweener.startTween(&value, 5.0f, 10.0f, 3, TweenTransition::Elastic, TweenEasing::EaseInOut);

// Start tween and get ID to determine when complete
TweenID tweenID = tweener.startTween(&secondValue, 7.0f, 11.0f, 4, TweenTransition::Sine, TweenEasing::EaseOut);

...
  // Update loop
  tweener.update(deltaTime);

  if (tweener.isTweenFinished(tweenID))
    std::cout << "Tween secondValue is complete" << std::endl;
```
