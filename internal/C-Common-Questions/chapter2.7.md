### 2.7 怎样建立和理解非常复杂的声明？例如定义一个包含 N 个指向返 回指向字符的指针的函数的指针的数组？
这个问题至少有以下 3 种答案:

1.char *(*(*a[N])())();

2.用 typedef 逐步完成声明:

    typedef char *pc;       /* 字符指针           */
    typedef pc fpc();       /* 返回字符指针的函数 */
    typedef fpc *pfpc;      /* 上面函数的指针     */
    typedef pfpc fpfpc();   /* 返回函数指针的函数 */
    typedef fpfpc *pfpfpc;  /* 上面函数的指针     */
    pfpfpc a[N];	    /* 上面指针的数组     */
    
3.使用 cdecl 程序, 它可以把英文翻译成 C 或者把 C 翻译成英文:

    cdecl> declare a as array of pointer to function returning
       pointer to function returning pointer to char
    char *(*(*a[])())()
    
通过类型转换, cdecl 也可以用于解释复杂的声明, 指出参数应该进入哪一对括号  (如同在上述的复杂函数定义中)。参见问题 [18.1](chapter18.1)。
一本好的 C 语言书都会解释如何 ``从内到外'' 解释和理解这样复杂 的 C 语言声明 (``模拟声明使用'')。
上文的例子中的函数指针声明还没有包括参数类型信息。如果参数有复杂类型, 声明就会变得真正的混乱了。现代的 cdecl 版本可以提供帮助。
