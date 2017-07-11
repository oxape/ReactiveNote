# interval

原型:
    
    public static func interval(_ period: RxTimeInterval, scheduler: SchedulerType)
示例:
        Observable<Int>
        .interval(1, scheduler: MainScheduler.instance)
        .subscribe(onNext: {
            print($0)
        })
输出:

    0
    1
    2
    3
    4
    5
    6
    7
interval会以period为周期连续发送元素