##### **问题**：如何实现一个高效的单向链表逆序输出？ 

##### **出题人**：阿里巴巴出题专家：昀龙／阿里云弹性人工智能负责人

##### **参考答案**：下面是其中一种写法，也可以有不同的写法，比如递归等。供参考。


```
typedef struct node{
    int           data;
    struct node*  next;
    node(int d):data(d), next(NULL){}
}node;

void reverse(node* head)
{
    if(head == NULL){
        return;
    }

    node* pleft = NULL;
    node* pcurrent = head;
    node* pright = head->next;

    while(pright){
        pcurrent->next = pleft;
        node *ptemp = pright->next;
        pright->next = pcurrent;
        pleft = pcurrent;
        pcurrent = pright;
        pright = ptemp;
    }

    while(pcurrent != NULL){
        cout<< pcurrent->data << "\t";
        pcurrent = pcurrent->next;
    }
}

```

``` java
class Solution<T> {

    public void reverse(ListNode<T> head) {
       if (head == null || head.next == null) {
    	   return ;
       }
       ListNode<T> currentNode = head;
       Stack<ListNode<T>> stack = new Stack<>();
       while (currentNode != null) {
    	   stack.push(currentNode);
    	   ListNode<T> tempNode = currentNode.next;
    	   currentNode.next = null; // 断开连接
    	   currentNode = tempNode;
       }
       
       head = stack.pop();
       currentNode = head;
       
       while (!stack.isEmpty()) {
    	   currentNode.next = stack.pop();
    	   currentNode = currentNode.next;
       }
    }
}

class ListNode<T>{
	T val;
	public ListNode(T val) {
		this.val = val;
	}
	ListNode<T> next;
}
```
