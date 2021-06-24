# 38. 动态规划案例分析

- 大盗潜入博物馆，有5件宝物，分别由重量和价值，大盗背包仅能负重20公斤，请如何选择宝物，总价值最高？

    [大盗问题](38%20%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92%E6%A1%88%E4%BE%8B%E5%88%86%E6%9E%90%200157dcfbc7d14a5f8dfaa9eafbecd78e/%E5%A4%A7%E7%9B%97%E9%97%AE%E9%A2%98%207c754171c28744669ffcaaf77ae60dea.csv)

    ```python
    # #博物馆大盗问题
    # ##动态规划解法
    # #宝物的重量和价值
    tr=[None,{'w':2,'v':3},{'w':3,'v':4},
             {'w':4,'v':8},{'w':5,'v':8},
             {'w':9,'v':10}]
    #大盗最大承重
    max_w=20
    # #初始化二维表格m[(i,w)]
    # #表示前i个宝物中，最大重量w的组合，所得到的最大价值
    # #当i什么都不取，或w上限为0，价值均为0
    m={(i,w):0 for i in range(len(tr))#len(tr)是6
                 for w in range(max_w+1)}
    # #逐个填写二维表格
    for i in range(1,len(tr)):
        for w in range(1,max_w+1):
            if tr[i]['w']>w:#装不下第i个宝物
                m[(i,w)]=m[(i-1,w)]#不装第i个宝物
            else:
                m[(i, w)] =max(
                    m[(i - 1, w)],
                    m[(i-1,w-tr[i]['w'])]+tr[i]['v'])
    # #输出结果
    print(m[(len(tr)-1,max_w)])
    ```

    用递归的方法

    ```python
    #递归解法
    #宝物的重量和价值，元组的集和
    tr={(2,3),(3,4),(4,8),(5,8),(9,10)}
    max_w=20
    #初始化记忆化表格m
    #key是（宝物组合，最大重量），value是最大价值
    m={}
    def thief(tr,w):
        if tr==set() or w==0:
            m[tuple(tr),w]=0#tuple是key的要求
            return 0#基本结束条件
        elif (tuple(tr),w) in m:
            return m[tuple(tr),w]
        else:
            vmax=0
            for t in tr:
                if t[0]<=w:
                    #逐个从集合中去掉某个宝物，递归调用
                    #选出所有价值中最大值
                    v=thief(tr-{t},w-t[0])+t[1]
                    vmax=max(vmax,v)
            m[tuple(tr),w]=vmax
            return vmax
    print(thief(tr,max_w))
    ```

---