

#pd.Series(data,index)
	## data可以是任意数据对象，(字典、列表、 NumPy 数组等等)
	## index 相当于标签  是对data的索引值 类似于key
	## index可以省略 并默认给予[0,.....,len(data)-1]
	## Pandas会自动把字典的键值设置成 Series 的 index，
	## 并将对应的 values 放在和索引对应的 data 里

	###classs = ['class1','class2','class3']
	###score = [96,97,98]
	###print(pd.Series(score,classs))
	
	###nparr = np.array(score)
	###print(pd.Series(nparr))
	###series1 = pd.Series([1,2,3,4],['A','B','C','D'])
	###print(series1['A'])
	### my_series[‘x’] 访问series数据格式
	

series的计算支持 +-*/  索引 相同的index  浮点运算data
进行计算的两个 Series 必须相同，不相同的 index，返回空值 NaN
	##series_A = pd.Series([2,3,4],['class1','class2','class3'])
	##series_B = pd.Series([1,2,3],['class1','class2','class3'])
	##print(series_A - series_B)

#pd.DataFrame(data,index)
	##数据表，类似于Excel  行和列组成
	##选用数据 修改索引 多重筛选（选定自己想要的行和列）
	##在DataFrame中 一个series 代表一列  多个series组成DataFrame
	##列名为Series名 行名为index
	##DF = {'Name':pd.Series(['ali','tencent','uber'],index=['A','B','C']),
      # 'Location':pd.Series(['hangzhou','shenzhen','US'],index=['A','B','C']),
      # 'Founders':pd.Series(['Jack ma','Pony','Travis'],index=['A','B','C'])}
      
      
#print(pd.DataFrame(DF))

	##将字典与index组合 形成表格
	##dic = {"Name":['GG','MM','KK'],
        "gender":["boy","girl","girl"],
        "age":[12,13,14],
       "year":[2018,2018,2018]
        }
	##table = pd.DataFrame(dic,index=['hangzhou',"shenzhen",'valley'])
	##print(table)

	##获取一列
	##print(table['learner'])
	##获取多个列 多个[]
	##print(table[['learner','age']])


#增减数据

	##增加数据
	###1.定义新的pd.Series 插入DataFrame中
	###2.通过现有的数据产生新数据 (类似Excel的公式计算)
	
	###table['prefer'] = pd.Series(['candy','cola','ice-###	cream'],index=['hangzhou',"shenzhen",'valley'])
	###pd.DataFrame(table)
	###	print(table)
	
	##table['Birth_year'] = table['year'] - table['age']
	##pd.DataFrame(table)
	##print(table)


	##删除数据
	###df.drop(,axis=)函数 行与列要指明 axis=0,row行  axis=1,columm列
	### 加上 inplace = True 才会真正删除数据
	###table.drop('Birth_year',axis=1,inplace=True)
	###pd.DataFrame(table)
	###print(table)




#获取数据
	##用.loc[]索引标签名, 或者 用.iloc[]按照行数来应用数据

	##df.loc[a]
	##df.loc[0,1]
	##df.loc['hangzhou'].loc['A']

	##同时 .loc[]也可以用来获取具体行列 生成子数据集
	##df.loc['A','hangzhou']
	##多行多列
	##df.loc(['B','C'],['hanghzou','shenzhen'])



#条件筛选
	##	用[]来接收条件语句 可以多接收一个 [xx][xxx]
	##df = pd.DataFrame(np.random.radin[5,4],['A','B','C','D','E'],['W','X','Y','Z'])

	##df[df.['w']>0]['x']>0
	##df[df.[['w']>0]['X''Y']]

	##&与|可以用于连接多个条件语句 一次应用多个筛选
	##df[(df['w']>0])&(df.['w']>1)



#重置索引
 	##.reset_index()把原索引放到index列中，将索引变成[0,....,len(data)-1]
	##与删除相同 需要用inplace=True 才会真正删除
 



#设置索引
	##set.index() 将某一列作为索引来引用  并且它会覆盖原来的索引值 无备份
	##set.index(hanghzou)

#多级索引 还没搞明白嘻嘻
	##.index.names可以用于给多级索引生成的索引命名 给它们加上名字
	##df.index.names = ['AA','BB']

#获取多级索引的特定数据
	##df.xs(22,level='Num')



#清洗数据
##删除或者填充空值
	##出现空值时，pandas.DataFrame会自动填充NaN or Null 
 	##可以调用.dropna()来丢弃自动填充的值 
 	##也可以调用.fillna()自动填充空值和填充数据
 
 	##.dropna(axis=0)为删除列
 	##.dropna(axis=1)为删除行   没有axis 默认删除行
 
	 ##.fillna() 填上指定默认值 
	 ##.fillna('20') 所有NaN填20
	 ##指定填充某些部位  df['A'].fillna(df.['A'].mean()) 在A列填充A列的平均值
 
	 ##inplace=True在这里同样适用

















