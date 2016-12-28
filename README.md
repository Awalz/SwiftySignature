<h1 align="center">SwiftySignature</h1>

<p align="center">
    <img src="https://img.shields.io/badge/platform-iOS%208%2B-blue.svg?style=flat" alt="Platform: iOS 8+"/>
    <a href="https://developer.apple.com/swift"><img src="https://img.shields.io/badge/language-swift%203-4BC51D.svg?style=flat" alt="Language: Swift 3" /></a>
    <a href="https://cocoapods.org/pods/SwiftySignature"><img src="https://img.shields.io/cocoapods/v/SwiftySignature.svg?style=flat" alt="CocoaPods compatible" /></a>
    <img src="http://img.shields.io/badge/license-BSD-lightgrey.svg?style=flat" alt="License: BSD" /> <br><br>
</p>

## Overview

SwiftySignature is a a lightweight signature capturing framework written in Swift. SwiftySignature utilizeds the [SwiftyDraw](https://github.com/Awalz/SwiftyDraw) drawing framework to get accurate, smooth drawings. 

## Requirements
* iOS 8.0+
* Swift 3.0

## License

SwiftySignature is available under the BSD license. See the LICENSE file for more info.

## Installation

### Cocoapods:

SwiftySignature is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "SwiftySignature"
```

### Manual Installation:

Simply copy the contents of the Source folder into your project.

## Usage

Using SwiftySignature is very simple:

### Getting Started:

Simple create a new SignatureView either through interface builder, or through code:

    let signatureView = SignatureView(frame: frame)
    self.view.addSubview(signatureView)
    
By default, the view will automatically respond to touch gestures and begin drawing. Drawing can be disbaled by the **drawingEnabled** property. 

### Capturing a Signature

Once a user has finished with their signature, you can call the **captureSignature** function on the signature view. When this function is called, the **SignatureViewDelegate** method **SignatureViewDidCaptureSignature(view:signature:)** will return an optional **Signature**:

    func SignatureViewDidCaptureSignature(view: SignatureView, signature: Signature?) {
    	if signature != nil {
       	print(signature!) // 
       }
    }
    
The returned Signature object may be nil if the canvas is blank. This can be checked prior to calling **captureSignature** with the **signaturePresent** property.

The **Signature** object contains both the signature **image** and the **date** that the signature was captured. 

The SignatureView can be cleared entirely using the **clearCanvas** function:

    signatureView.clearCanvas()
    
## Properties

* **lineColor** - Signature stroke color. Accepts any UIColor. Default is black
* **lineWidth** - Signature stroke width. Accepts any positive CGFloat. Default is 3.0
* **lineOpacity** - Signature stroke opacity. Accepts a CGFloat between 0.0 and 1.0
* **signaturePresent** (get-only) - Returns whether a signature is present or not. 
* **signatureIsOpaque** - Sets whether or not the Signature image is on an opaque, white, background or transparent
    
## Delegate 

* **SignatureViewDidCaptureSignature(view:signature:)** - Called when the **captureSignature** function is called. Returns an optional **Signature** object
* **SignatureViewDidBeginDrawing(view:)** - Called when a user begins drawing a line segment on the SignatureView. Can be called multiple times.
* **SignatureViewIsDrawing(view:)** - Called when a user is drawing on the SignatureView. Will be called multiple times
* **SignatureViewDidFinishDrawing(view:)** - Called when a user finished drawing a line segment. Can be called mulitple times
* **SignatureViewDidCancelDrawing(view:)** - Called when a user cancels drawing a line segment

## Contact

If you have any questions, requests, or enhancements, feel free to submit a pull request, create an issue, or contact me in person:

**Andrew Walz**
**andrewjwalz@gmail.com**

