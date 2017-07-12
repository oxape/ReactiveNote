# delay
原型:

    public func delay(_ dueTime: RxTimeInterval, scheduler: SchedulerType) -> RxSwift.Observable<Self.E>

示例:

        Observable<Int>
        .interval(0.1, scheduler: MainScheduler.instance)
        .take(3)
        .do(onNext: { interval in
            print("do \(interval) " + "\(NSDate())")
        })
        .delay(1, scheduler: MainScheduler.instance)
        .subscribe(onNext: { elemnt in
            print("delay \(elemnt) " + "\(NSDate())")
        })

输出:

    do 0 2017-07-12 09:10:11 +0000
    do 1 2017-07-12 09:10:11 +0000
    do 2 2017-07-12 09:10:11 +0000
    delay 0 2017-07-12 09:10:12 +0000
    delay 1 2017-07-12 09:10:12 +0000
    delay 2 2017-07-12 09:10:12 +0000

delay的作用就是的对每个发射的信号延时

