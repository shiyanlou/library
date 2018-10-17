### 2.6 我似乎不能成功定义一个链表。我试过  typedef struct { char *item; NODEPTR next; } *NODEPTR; 但是编译器报了错误信息。难道在C语言中一个 结构不能包含指向自己的指针吗？
C 语言中的结构当然可以包含指向自己的指针; [K&R2, 第 6.5 节] 的讨论 和例子表明了这点。 NODEPTR 例子的问题是在声明 next 域的时候  typedef 还没有定义。为了解决这个问题, 首先赋予这个结构一个标签  (struct node)。然后, 声明 next 域为 struct node, 或者分开 typedef 定义和结构定义, 或者两者都采纳。 以下是一个修改后的版本:

	struct node {
	    char *item;
	    struct node *next;
	};

	typedef struct node *NODEPTR;
至少还有三种同样正确的方法解决这个问题。
在用 typedef 定义互相引用的两个结构时也会产生类似的问题, 可以用同样的方法解决。
参见问题 [2.1](chapter2.1.md)。
