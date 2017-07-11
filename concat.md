# concat

原型: 

	public func concat<O>(_ second: O) -> RxSwift.Observable<Self.E> where O : ObservableConvertibleType, O.E == Self.E
示例:

	Observable<Int>
	.interval(1, scheduler: MainScheduler.instance)
	.take(3)
	.concat(Observable<Int>.interval(0.01, scheduler: MainScheduler.instance).take(10))
	.subscribe({ event in
		print(event)
	})
输出:

    next(0)
    next(1)
    next(2)
    next(0)
    next(1)
    next(2)
    next(3)
    next(4)
    next(5)
    next(6)
    next(7)
    next(8)
    next(9)
    completed

concat会把second连接到源Stream后面，注意是Stream发送competed才会连接后面的second才会发射元素。
下面的代码永远不会收到secondButton的点击事件，因为UIButton的tap永远不会发送competed事件。

    button.rx.tap.concat(secondButton.rx.tap).subscribe(onNext: {
    	print($0)
    }).addDisposableTo(disposeBag)

如下代码会收到button的一次点击事件，点击一次button，然后点击secondButton可以收到secondButton的事件。但是在点击button前不会收到secondButton的点击事件。

    button.rx.tap.take(1).concat(secondButton.rx.tap).subscribe(onNext: {
        print($0)
    }).addDisposableTo(disposeBag)
