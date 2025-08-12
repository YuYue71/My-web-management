---
title: C# 語法語常用函式
date: 2025-08-12 17-59-59
categories: 教學筆記
cover: https://tse4.mm.bing.net/th/id/OIP.zMf51808IUGtdgUpDyV13QHaEK?cb=thvnextc2&rs=1&pid=ImgDetMain&o=7&rm=3
tags: [CSharp,語法,函示,教學]
---

## 流程控制與語法結構
> `if (條件) { }                `   -> 條件判斷
> `else if (條件) { }           `   -> 否則如果
> `else { }                     `   -> 否則
> `switch (變數) { case x: ... }`   -> 多分支
> `for (int i=0;i<n;i++) { }    `   -> for 迴圈
> `foreach (var item in col) { }`   -> 遍歷集合
> `while (條件) { }             `   -> 當條件成立
> `do { } while (條件);         `   -> 先做再判斷
> `break;                       `   -> 中斷迴圈
> `continue;                    `   -> 跳過當次迭代
> `return 值;                   `   -> 從方法返回
> `goto 標籤;                   `   -> 跳到指定位置（不建議）
> `try { } catch { }            `   -> 捕捉例外
> `try { } catch { } finally { }`   -> 捕捉並處理後續
> `throw new Exception(msg);    `   -> 拋出例外
> `using(var obj = new ...){ }  `   -> 自動釋放資源

---

## 例外處理
> `try { ... } `
> `catch (Exception ex) { ... }` -> 捕捉例外
> `finally { ... }             ` -> 必執行區塊
> `throw new Exception(msg);   ` -> 拋出例外

---

## 數學與亂數 (System.Math, System.Random)
> `Math.Abs(x)             `       -> 傳回絕對值
> `Math.Pow(a,b)           `       -> a 的 b 次方
> `Math.Sqrt(x)            `       -> 平方根
> `Math.Ceiling(x)         `       -> 無條件進位
> `Math.Floor(x)           `       -> 無條件捨去
> `Math.Round(x)           `       -> 四捨五入
> `Math.Truncate(x)        `       -> 截斷小數部分
> `Math.Sign(x)            `       -> 判斷正負號（-1,0,1）
> `Math.Max(a,b)           `       -> 較大值
> `Math.Min(a,b)           `       -> 較小值
> `Math.Sin(x)             `       -> 正弦
> `Math.Cos(x)             `       -> 餘弦
> `Math.Tan(x)             `       -> 正切
> `Math.Asin(x)            `       -> 反正弦
> `Math.Acos(x)            `       -> 反餘弦
> `Math.Atan(x)            `       -> 反正切
> `Math.Atan2(y,x)         `       -> 傳回對應象限的反正切
> `Math.Log(x)             `       -> 自然對數
> `Math.Log10(x)           `       -> 以10為底對數
> `Math.Exp(x)             `       -> e 的 x 次方
> `Math.Clamp(val,min,max) `       -> 限制範圍（C# 8+）
> `Random r = new Random();`       -> 建立亂數物件
> `r.Next()                `       -> 產生整數
> `r.Next(min,max)         `       -> 產生指定範圍整數
> `r.NextDouble()          `       -> 0~1 隨機浮點數

---

## 字串處理 (string 類別)
> `str.Length                  `  -> 字串長度
> `str.ToUpper()               `  -> 轉成大寫
> `str.ToLower()               `  -> 轉成小寫
> `str.Trim()                  `  -> 去除前後空白
> `str.TrimStart()             `  -> 去除前端空白
> `str.TrimEnd()               `  -> 去除尾端空白
> `str.Replace(a,b)            `  -> 替換字串
> `str.Contains(x)             `  -> 是否包含子字串
> `str.StartsWith(x)           `  -> 是否以指定字串開頭
> `str.EndsWith(x)             `  -> 是否以指定字串結尾
> `str.IndexOf(x)              `  -> 找出子字串位置
> `str.LastIndexOf(x)          `  -> 從後面開始找
> `str.Substring(i,len)        `  -> 擷取子字串
> `str.Split(',')              `  -> 分割字串
> `str.Join(",",arr)           `  -> 陣列合併成字串
> `string.IsNullOrEmpty(s)     `  -> 是否為 null 或空字串
> `string.IsNullOrWhiteSpace(s)`  -> 是否為 null 或全是空白
> `str.PadLeft(10,'0')         `  -> 左側補滿指定長度
> `str.PadRight(10,' ')        `  -> 右側補滿指定長度
> `str.Insert(index,value)     `  -> 插入字串
> `str.Remove(index,len)       `  -> 刪除指定位置的子字串

---

## 正則表達式 (System.Text.RegularExpressions)
> `Regex.IsMatch(s, pattern)`   -> 是否符合模式
> `Regex.Match(s, pattern)  `   -> 傳回第一個匹配
> `Regex.Matches(s, pattern)`   -> 傳回所有匹配
> `Regex.Replace(s, p, r)   `   -> 取代
> `Regex.Split(s, pattern)  `   -> 分割

---

## 集合操作 (List, Dictionary, Array, LINQ)
> `List<T>.Add(x)                  ` -> 新增元素
> `List<T>.AddRange(col)           ` -> 新增多個元素
> `List<T>.Remove(x)               ` -> 移除元素
> `List<T>.RemoveAt(i)             ` -> 移除指定位置
> `List<T>.Clear()                 ` -> 清空
> `List<T>.Contains(x)             ` -> 是否包含元素
> `List<T>.Count                   ` -> 元素數量
> `List<T>.Sort()                  ` -> 排序
> `List<T>.Reverse()               ` -> 反轉
> `List<T>.IndexOf(x)              ` -> 取得索引
> `List<T>.Find(p=>p>5)            ` -> 找第一個符合條件的元素
> `List<T>.FindAll(p=>p>5)         ` -> 找所有符合條件的元素
> `Dictionary<K,V>.Add(k,v)        ` -> 新增鍵值
> `Dictionary<K,V>.Remove(k)       ` -> 移除鍵
> `Dictionary<K,V>.ContainsKey(k)  ` -> 是否有該鍵
> `Dictionary<K,V>.ContainsValue(v)` -> 是否有該值
> `Array.Sort(arr)                 ` -> 陣列排序
> `Array.Reverse(arr)              ` -> 陣列反轉
> `arr.Length                      ` -> 陣列長度
> `arr.Clone()                     ` -> 陣列複製
> `Enumerable.Where(...)           ` -> 篩選
> `Enumerable.Select(...)          ` -> 映射轉換
> `Enumerable.Any(...)             ` -> 是否有符合條件的元素
> `Enumerable.All(...)             ` -> 是否全部符合條件
> `Enumerable.Sum(...)             ` -> 總和
> `Enumerable.Average(...)         ` -> 平均
> `Enumerable.Max(...)             ` -> 最大值
> `Enumerable.Min(...)             ` -> 最小值

---

## 檔案與 I/O
> `Console.WriteLine(x)           ` -> 輸出文字
> `Console.Write(x)               ` -> 輸出不換行
> `Console.ReadLine()             ` -> 讀取一行輸入
> `Console.ReadKey()              ` -> 讀取按鍵
> `File.Exists(path)              ` -> 檢查檔案是否存在
> `File.ReadAllText(path)         ` -> 讀取整個文字檔
> `File.WriteAllText(path,str)    ` -> 覆蓋寫入文字檔
> `File.AppendAllText(path,str)   ` -> 附加寫入文字檔
> `File.Copy(src,dst)             ` -> 複製檔案
> `File.Delete(path)              ` -> 刪除檔案
> `Directory.Exists(path)         ` -> 檢查資料夾是否存在
> `Directory.CreateDirectory(path)` -> 建立資料夾
> `Directory.Delete(path)         ` -> 刪除資料夾
> `Directory.GetFiles(path)       ` -> 取得資料夾檔案
> `Directory.GetDirectories(path) ` -> 取得子資料夾
> `Path.Combine(a,b)              ` -> 合併路徑
> `Path.GetExtension(path)        ` -> 取得副檔名
> `Path.GetFileName(path)         ` -> 取得檔名
> `Path.GetDirectoryName(path)    ` -> 取得資料夾路徑

---

## 日期與時間 (DateTime, TimeSpan)
> `DateTime.Now          `          -> 現在日期時間
> `DateTime.Today        `          -> 今天日期
> `DateTime.UtcNow       `          -> UTC 現在時間
> `DateTime.AddDays(n)   `          -> 增加/減少天數
> `DateTime.AddMonths(n) `          -> 增加/減少月份
> `DateTime.AddYears(n)  `          -> 增加/減少年份
> `DateTime.AddHours(n)  `          -> 增加/減少小時
> `DateTime.AddMinutes(n)`          -> 增加/減少分鐘
> `DateTime.AddSeconds(n)`          -> 增加/減少秒
> `DateTime.Subtract(dt) `          -> 減去另一時間
> `DateTime.ToString(fmt)`          -> 格式化日期字串
> `TimeSpan.FromDays(x)  `          -> 建立以天為單位的時間間隔
> `TimeSpan.FromHours(x) `          -> 建立以小時為單位的時間間隔
> `TimeSpan.TotalMinutes `          -> 總分鐘數
> `TimeSpan.TotalSeconds `          -> 總秒數

---

## 委派與事件
> `delegate void MyDelegate();`  -> 定義委派
> `MyDelegate d = Method;     `  -> 建立委派
> `event EventHandler Click;  `  -> 事件定義

---

## 非同步與多執行緒
> `Task.Run(() => {...});        `   -> 建立任務
> `await Task.Delay(1000);       `   -> 延遲
> `Thread t = new Thread(Method);`
> `t.Start();                    `   -> 啟動執行緒
> `Parallel.For(0,10,i=>{...});  `   -> 平行迴圈

---

## 反射
> `typeof(string)                 `  -> 取得型別物件
> `obj.GetType()                  `  -> 執行期型別
> `Assembly.GetExecutingAssembly()`  -> 當前組件

---

## 序列化
> `JsonSerializer.Serialize(obj)      `   -> 物件轉 JSON
> `JsonSerializer.Deserialize<T>(json)`   -> JSON 轉物件