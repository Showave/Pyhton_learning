# Pyhton_learning
learning for Python
一、 设置默认参数
 必选参数在前，默认参数在后
 变化大的参数放前面
    好处：降低调用函数的难度
    注意：默认参数必须指向不变对象！
*nums表示取nums这个list的所有元素。
二、 可变参数：*args , 允许传入0-任意个参数def sum(*args)
三、 关键字参数：def person(name, age, **kw) ，传入0个或任意个含参数名的参数，并自动组装为一个dict。
        命名关键字参数def person(name, age, *, city, job)
参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数。
四、 切片操作，倒数一个元素是-1。 代替循环，注意多加运用。 前十个数，每隔两个取一个 L[:10:2]
五、 迭代：默认情况下，dict迭代的是key，要迭代value：for value in d.values()；同时迭代key、value：for k, v in d.items()。  python内置enumerate函数可以将list变成num-key对。
提交六、列表生成式（快速生成list）：print([d for d in os.listdir('.')])，要生成的元素d放在for前面。列出当前目录下的所有文件和目录名
          [s.lower() for s in L] 将list中的所有字符串变成小写
七、生成器：g = (x * x for x in range(10)) ，（）。generator，包含yield关键字，每次调用next（）执行，遇到yield返回，再次执行时从上次yield处继续执行。
八、map/reduce:
          map：有两个参数，返回一个list。r = map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9]),f是函数对象本身。f(x)=x2； list(map(str, [1, 2, 3, 4, 5, 6, 7, 8, 9])),将list中所有数字转换成字符串。
          reduce：有两个参数，将结果和序列的下一个元素继续做累计计算，reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4)

九、 filter()用于过滤序列，类似map，参数为一个函数和一个序列。将传入的函数作用于序列每个元素，根据返回值T or F决定保留元素。 filter()使用了惰性计算，只有在取结果时，才真正开始筛选并每次返回下一个筛选出的元素。
十、sorted()是高阶函数，接收一个key函数实现自定义的排序。例如按绝对值排序：sorted（【1，-10,10】，key=abs）,key=str.lower:大写转为小写;第三个参数反向排序reversr=true。
十一、返回函数，并未执行，函数中不要用可能变化的变量。
十二、匿名函数lambda x: x * x、只有一个表达式，不用写return。好处：不必担心函数名冲突。可以匿名函数赋值给一个变量f = lambda x: x * x，f(5)调用。
十三、 @log的Decorator
十四、 偏函数functools.partial，import functools    int2 = functools.partial(int, base=2)。把一个函数的某些参数给固定住（也就是设置默认值），返回一个新的函数，调用这个新函数会更简单。
十五、 使用模块：__xxx__特殊变量，一般不用。_xxx的函数或变量是private，不被直接引用。def _private_1(name):
    return 'Hello, %s' % name
十六、 class和实例class Student(object): ，class声明类Student继承object类，__init__的第一个参数永远是self，表示创建的实例本身，因此，在__init__内部，就可以把各种属性绑定到self
十七、 内部变量：在属性的名称前面加两个下划线__，self.__name = name。外部代码如果要获取name：增加get_name（self）：return self._name ，修改内部私有变量：set_score(self,score): self._score = score
十八、 判断一个变量是否是某个类型可以用isinstance()判断：isinstance(a, list) ->True
十九、 获得一个对象的所有属性和方法：dir（），返回一个包含字符串的list
二十、 len（‘ABC’）等价于‘ABC’.__len__()
二十一、 getattr()、setattr()以及hasattr()，我们可以直接操作一个对象的状态
二十二、 __slots__ = ('name', 'age') # 用tuple定义允许绑定的属性名称
二十三、 @property装饰器就是负责把一个方法变成属性调用的，用在类的定义中，
24. 多重继承：class Dog(Mammal, Runnable)，一个子类可以同时获得多个父类的所有功能。
25. 如果一个类想被用于for ... in循环，类似list或tuple那样，就必须实现一个__iter__()方法，
26. 任何类，只需要定义一个__call__()方法，就可以直接对实例进行调用。调用： s（）
27. 使用枚举类，Enum，from enum import Enum，Month = Enum('Month', ('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))
28. type()函数可以查看一个类型或变量的类型
29. try...except...finally用来处理错误
30. 断言，assert n ！= 9，$ python -O err.py 关闭全局assert
31. with open('/path/to/file', 'r') as f:    ###自动调用close（）方法；读取图片、视频，参数‘r’->‘rb’
        print（f.read()）     ###如果文件较大，可以反复调用read（size），readlines（）一次读取所有能容返回list
    f = open('/Users/michael/gbk.txt', 'r', encoding='gbk', errors='ignore') ###打开gnk格式文件，忽略期中的字符错误
    使用with语句操作文件IO是个好习惯。
32. # 查看当前目录的绝对路径: >>> os.path.abspath('.')
    # 在某个目录下创建一个新目录，首先把新目录的完整路径表示出来: os.path.join('/Users/michael', 'testdir')
    # 拆目录 >>> os.path.split('/Users/michael/testdir/file.txt')  output》》('/Users/michael/testdir', 'file.txt')
# os.path.splitext()可以直接让你得到文件扩展名 >>> os.path.splitext('/path/to/file.txt') 》》('/path/to/file', '.txt')
       # 对文件重命名: >>> os.rename('test.txt', 'test.py')
       # 删掉文件: >>> os.remove('test.py')
    # 列出当前目录下的所有目录 >>> [x for x in os.listdir('.') if os.path.isdir(x)]
33.序列化：把变量从内存中变成可存储或传输的过程称之为序列化，在Python中叫pickling，在其他语言中也被称之为serialization，marshalling，flattening；反过来，把变量内容从序列化的对象重新读到内存里称之为反序列化，即unpickling。
         JSON表示的对象就是标准的JavaScript语言的对象，dumps()方法返回一个str，内容就是标准的JSON
     通常class的实例都有一个__dict__属性，它就是一个dict，用来存储实例变量。也有少数例外，比如定义了__slots__的class。
     print(json.dumps(s, default=lambda obj: obj.__dict__))  ##s为class的实例
     class实例的反序列化print(json.loads(json_str, object_hook=dict2student)
34. multiprocessing：   
     from multiprocessing import Process  
     p = Process(target=run_proc, args=('test',))  ##创建子进程，只需要传入一个执行函数和函数的参数
     p.start()   ##并创建一个process实例，用start方法启动子进程
     Pool（进程池）：
     from multiprocessing import Pool  ##导入pool类
     p = Pool(4)
     for i in range(5):
          p.apply_async(long_time_task, args=(i,))  ##     
    p.close()
    p.join()  ##对pool对象调用join（）方法会等待所以进程执行完毕，调用join前必须先调用close（）。
     chlid process（子进程）：
     subprocess模块可以让我们非常方便地启动一个子进程，然后控制其输入和输出。##nslookup 查找域名Ip地址
     进程间通信：
     from multiprocessing import Process, Queue  
     q = Queue（）  ##q.put()   q.get(value)
35.多线程：启动一个线程就是把一个函数传入并创建Thread实例，然后调用start()开始执行：
     t = threading.Thread(target=loop, name='LoopThread')  ##target is fun
     t.start()   
Python的threading模块有个current_thread()函数，它永远返回当前线程的实例。主线程实例的名字叫MainThread，子线程的名字在创建时指定，我们用LoopThread命名子线程。
     线程锁（LOCK）：
          lock = threading.Lock()
          lock.acquire()  ##获取锁
          .......
          lock.release()   ##释放锁
     Pthon解释器由于设计时有GIL全局锁，导致了多线程无法利用多核。多线程的并发在Python中就是一个美丽的梦。
     
全局变量local_school就是一个ThreadLocal对象，每个Thread对它都可以读写student属性，但互不影响。你可以把local_school看成全局变量，但每个属性如local_school.student都是线程的局部变量，可以任意读写而互不干扰，也不用管理锁的问题，ThreadLocal内部会处理。

可以理解为全局变量local_school是一个dict，不但可以用local_school.student，还可以绑定其他变量，如local_school.teacher等等。

ThreadLocal最常用的地方就是为每个线程绑定一个数据库连接，HTTP请求，用户身份信息等，这样一个线程的所有调用到的处理函数都可以非常方便地访问这些资源。
ThreadLocal解决了参数在一个线程中各个函数之间互相传递的问题
36.正则表达式：
    s = r'ABC\-001' # Python的字符串 r前缀，不用考虑转义
     test = '用户输入的字符串'
     if re.match(r'正则表达式', test):
         print('ok')
     else:
         print('failed')
     切分：
          >>> re.split(r'[\s\,\;]+', 'a,b;; c  d') ##去掉空格、逗号、分号
          ['a', 'b', 'c', 'd']
     分组：
     ﻿
          m = re.match(r'^(\d{3})-(\d{3,8})$', '010-12345')﻿
         m.group(0) ##可以在Match对象上用group()方法提取出子串来。
37.datetime表示的时间需要时区信息才能确定一个特定的时间，否则只能视为本地时间。
38.
collections：
     namedtuple是一个函数，它用来创建一个自定义的tuple对象，并且规定了tuple元素的个数，并可以用属性而不是索引来引用tuple的某个元素。
     我们用namedtuple可以很方便地定义一种数据类型，它具备tuple的不变性，又可以根据属性来引用，使用十分方便。     deque是为了高效实现插入和删除操作的双向列表，适合用于队列和栈：deque除了实现list的append()和pop()外，还支持appendleft()和popleft()，这样就可以非常高效地往头部添加或删除元素
     defaultdict如果希望key不存在时，返回一个默认值，就可以用defaultdict：
     OrderedDict的Key会按照插入的顺序排列，不是Key本身排序
39.struct的pack函数把任意数据类型变成bytes：
40. chain()可以把一组迭代对象串联起来，形成一个更大的迭代器：for c in itertools.chain('ABC', 'XYZ'):
         groupby()把迭代器中相邻的重复元素挑出来放在一起：for key, group in itertools.groupby('AAABBBCCAAA'):
41.   hashlib：db[username] = get_md5(password + username + 'the-Salt')    ##摘要算法，不是加密算法，不能用于加密，只能用于防篡改
        hmac：h = hmac.new(key, message, digestmod='MD5') ##比较加盐算法更安全，在计算哈希的过程中，将key混入计算过程中。

