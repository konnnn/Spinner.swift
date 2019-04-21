# Spinner.swift
How to make a reusable Activity Indicator with Swift

import UIKit

open class Spinner {
    
    internal static var spinner: UIActivityIndicatorView?
    public static var style: UIActivityIndicatorView.Style = .whiteLarge
    public static var baseBackColor = UIColor.black.withAlphaComponent(0.5)
    public static var baseColor = UIColor.white
    
    public static func start(style: UIActivityIndicatorView.Style = style, backgroundColor: UIColor = baseBackColor, color: UIColor = baseColor) {
        if spinner == nil, let window = UIApplication.shared.keyWindow {
            let frame = UIScreen.main.bounds
            spinner = UIActivityIndicatorView(frame: frame)
            spinner?.backgroundColor = backgroundColor
            spinner?.style = style
            spinner?.color = color
            window.addSubview(spinner!)
            spinner?.startAnimating()
        }
    }
    
    public static func stop() {
        if spinner != nil {
            spinner?.stopAnimating()
            spinner?.removeFromSuperview()
            spinner = nil
        }
    }
    
}

To implement Spinner, just go to the View Controller. Then, in place where indicator should start animating (i.e. viewDidLoad or viewWillAppear) just put Spinner.start(). Or, if you want personalize style, backColor and/or baseColor:

override func viewDidLoad() {
        super.viewDidLoad()
        
        Spinner.start(style: .white, backgroundColor: UIColor.white, color: UIColor.red)
}

Then, in a place where processing is done, simply put: 
        Spinner.stop()


