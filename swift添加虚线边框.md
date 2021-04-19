### 绘制虚线边框

```
func addDottedBorderWithView(view:UIView,cornerRadius:CGFloat,strokeColor:UIColor) {
    let viewWidth:CGFloat = view.frame.size.width
    let viewHeight:CGFloat = view.frame.size.height
    view.layer.cornerRadius = cornerRadius
    let borderLayer:CAShapeLayer = CAShapeLayer.init()
    borderLayer.bounds = CGRect.init(x: 0, y: 0, width: viewWidth, height: viewHeight)
    borderLayer.position = CGPoint.init(x:view.bounds.midX , y: view.bounds.midY)
    borderLayer.path = UIBezierPath.init(roundedRect: borderLayer.bounds, cornerRadius: cornerRadius).cgPath
    borderLayer.lineWidth = 1
    borderLayer.lineDashPattern = [4, 4]
    borderLayer.fillColor = UIColor.clear.cgColor
    borderLayer.strokeColor = strokeColor.cgColor
    view.layer.addSublayer(borderLayer)
}
```
### 使用方式

```
lazy var cardIdButton:UIButton = {
    let btn = UIButton.init(frame: CGRect.init(x: 100, y: 100, width: 130, height: 46))
    btn.setTitle("＋ 输入标签", for: .normal)
    btn.setTitleColor(UIColor.blue, for: .normal)
    return btn
}();
override func viewDidLoad() {
    super.viewDidLoad()
    // Do any additional setup after loading the view.
    self.view.addSubview(cardIdButton)
    self.addDottedBorderWithView(view: cardIdButton, cornerRadius: 23, strokeColor: UIColor.blue)

}
```
