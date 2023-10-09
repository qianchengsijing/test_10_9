# test_10_9
#include <stdio.h>

#define MaxSize 255
struct TreeNode{
	int value;
	bool IsEmpty;
};
typedef struct BiTNode{
	ElemType data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
//先序遍历
void PreOrder(BiTree T){
	if(T != NULL){
		visit(T);
		PreOrder(T->lchild);
		PreOrder(T->rchild);
	}
}
//中序遍历
void InOrder(BiTree T){
	if(T != NULL){
		InOrder(T->lchild);
		visit(T);
		InOrder(T->rchild);
	}
}
//后序遍历
void PostOrder(BiTree T){
	if(T != NULL){
		PostOrder(T->lchild);
		PostOrder(T->rchild);
		visit(T);
	}
}
//求树的深度
int TreeDepth(BiTree T){
	if(T != NULL){
		return 0;
	}
	else{
		int l = TreeDepth(T->lchild);
		int r = TreeDepth(T->rchild);
		return l>r ? l+1 : r+1;
	}
}

//二叉树的层序遍历
typedef struct BiTNode{
	char data;
	struct BiTNode *lchild,*rchild;
}BiTNode,*BiTree;
typedef struct LinkNode{
	BiTNode* data;
	struct LinkNode* next;
}LinkNode;
typedef struct{
	LinkNode* Prior,*rear;
}LinkQueue;

void LevelOrder(BiTree T){
	LinkQueue Q;
	InitQueue(Q);
	BiTree p;
	EnQueue(Q,T);
	while(!IsEmpty(Q)){
		DeQueue(Q,p);
		visit(p);
		if(p->lchild != NULL)
			EnQueue(Q,T->lchild);
		if(p->rchild != NULL)
			EnQueue(Q,T->rchild);
	}
}
int main(){
  BiTree T;
  TreeNode T[MaxSize];
  return 0;
}
