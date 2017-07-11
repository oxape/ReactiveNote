# take

原型:

    public func take(_ count: Int) -> RxSwift.Observable<Self.E>

示例:

    Observable<Int>
    .interval(0.1, scheduler: MainScheduler.instance)
    .take(10)
    .subscribe({ event in
    	print(event)
    })

输出:

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

take会把Stream截取到count，并且在发射元素到达count限制时发送completed事件。