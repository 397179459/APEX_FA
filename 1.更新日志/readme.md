![](../img/1.apex_img/a1.PNG)

#### 记录更新日志

- 2019/8/22 

  **小坑：有个语句需要注意，神坑。**

  ```sql
  SUM(CASE 
      WHEN STATUS = '掌握' THEN 1 
      ELSE 0 
      END
     ) NOW
  --上面的这种写法现在有问题，需要用下面这种形式,
  SUM(CASE STATUS 
      WHEN '掌握' THEN 1 
      ELSE 0 
      END
     ) NOW
  ```

  

* 2019/7/21 

    * 增加技能树，主要用到`D3 Collapsible Tree Chart`插件
    * 主页增加按照具体分数分布图

* 2019/7/4 全面规范化SQL语句，之前只为了实现功能，没有注意缩进格式，重构后SQL嵌套比较清晰

* 2019/6/27 所有人员之前是乱序的，现在是按照组别排序的，修改的是 GROUP BY 和ORDER BY 的字段，注意还要修改一个设置：组合图属性中->多系列图标数据 选择 否，否则它会自动升序排列

* 2019/6/25 之前建表的时候有点问题，FA_NAME.LVL和SKILL_ALL.SKILL_LEVEL设置成了varchar2字段，导致对比的结果有问题，现在数据量太多了修改数据库不方便，所以直接修改4.7节的SQL语句
    ```sql
    ...
    --T2.SKILL_LEVEL <= T1.LVL
    TO_NUMBER(T2.SKILL_LEVEL) <= TO_NUMBER(T1.LVL)
    ...
    ```
    
* 2019/6/24 个人页面新增查看最后一次编辑时间功能，思路是在数据库新增一列来记录最后一次保存的日期，UPDATE触发事件是保存交互式报表

* 2019/5/26 第一版上线
----