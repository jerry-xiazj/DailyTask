# DailyTask

[toc]

## 1 介绍

**DailyTask**是用来管理任务的小型C++练习项目。任务有三种类型，可以增、删、改每个任务。

![界面](doc/example.png)

## 2 运行

使用 `C++ 11` 编译，如使用`gcc`:

```bash
// 编译
g++ -std=c++11 *.cpp -o DailyTask

// 运行
./DailyTask
```

## 3 用法

共有三种任务类型。每种任务提供了一个模板文件（*_template），用于向程序中增加任务。每种任务都有相应的基本操作。

名称     | 简介
:------:|:---------
 period | 每隔固定时间执行一次的循环性任务
 short  | 短期有起止日期的任务，可有多层
 temp   | 有明确任务量的任务，可设定预计完成日期

### 3.1 `period `型任务

- 模板文件见下方。
- 若超过`当前循环截止日期`而为完成当前循环任务，则任务进入`已过期`状态。需要修改循环截止日期已重新激活任务。

```
period              //period型任务
7 52 1              //循环周期，循环次数，已完成循环数
20181227            //当前循环截止日期
n                   //是否处于激活状态
0 period_work n     //任务层级（无用），任务名称，是否已完成（无用）
20181220 任务已完成  //已完成循环记录
```

### 3.2 `short`型任务

- 模板文件见下方。
- 任务最深为3级（`任务层级`=0,1,2）。

```
short               //short型任务
20181220 20181224 7 //开始时间，完成期限，任务数量
0 short_work_1 n    //任务层级，任务名称，是否已完成(下同)
1 step_1 n
1 step_2 n
2 sub_step_21 y
2 sub_step_22 n
0 short_work_2 y
1 step_1 y
```

### 3.3 `temp`型任务

- 模板文件见下方。

```
temp                            //temp型任务
477 764                         //已完成任务量，总任务量
20190131                        //预计完成时间
0 temp_work n                   //任务层级，任务名称，是否已完成
20181209 完成量：	7	447-454  //已完成任务记录
20181210 完成量：	5	454-459
20181212 完成量：	11	459-470
20181221 完成量：	7	470-477
```