# https-github.com-keepingtheway-
在面向对象编程中 我们时常调用equals方法对字符串进行比较
然而 当我们比较我们自定义类的对象时 调用 equals方法时却无法得到我们想要的结果
那是为什么呢？ 我们先来看一下Object中equals的用法
查阅API文档如下
https://github.com/keepingtheway/https-github.com-keepingtheway-/blob/master/QQ%E5%9B%BE%E7%89%8720190807193026.png
为何查阅Object类的equals方法呢？
是因为自定义的类会默认继承了Object类 在调用equals方法时 其实调用的基类Object中的方法 而上面API文档中说明了Object类中的equals方法比较的是地址
所以  解决方法就是在自定义类中重写equals方法
Animal A1=new Dog("lala");
		Animal A=new Dog("lala");
		System.out.println(A.equals(A1));//未重写Object中的equals方法时 比较的时对象的地址 为false
		String s=new String("jsk");
		String s1=new String("js");
		System.out.println(s.equals(s1));//String类中重写了equals方法 调用比较的对象中的值
  重写的equals方法如下
  @Override
	public boolean equals(Object obj){
		if (obj instanceof Dog) {
			Dog dog = (Dog) obj;
			return this.name.equals(dog.name);
		}
		return false;
		
	}
