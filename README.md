# POSist-Campus-Hiring

#include<bits/stdc++.h>
using namespace std;

struct node{
	
	struct timestamp{
		struct date{
			int day;
			int month;
			int year;
		};
		
		date d;
		
		struct time{
			int hrs;
			int minutes;
			int sec;
		};
		
		time t;
	};
	
	timestamp ti;
	
	struct data{
		string owner_name;
		string address;
		int mobile_no;
		int phone;
		float value;
	};
	
	data da;
	
	int node_number;
	static int node_id;
	node *reference_node_id;
	int child_id;
	node *reference_child_id;
};

void make_first_node(node**first_node)
{
	cin>>(*first_node)->ti.d.month;
	cin>>(*first_node)->ti.d.year;
	cin>>(*first_node)->ti.d.day;
			
	cin>>(*first_node)->ti.t.hrs;
	cin>>(*first_node)->ti.t.minutes;
	cin>>(*first_node)->ti.t.sec;
			
			
	cin>>(*first_node)->da.owner_name;
	cin>>(*first_node)->da.address;
	cin>>(*first_node)->da.mobile_no;
	cin>>(*first_node)->da.phone;
	cin>>(*first_node)->da.value;
			
	(*first_node)->node_number=1;
	(*first_node)->node_id=1;
	(*first_node)->child_id=0;
	(*first_node)->reference_child_id=NULL;

}

void append_fun(node**append_node,node**first_node)
{
	node*temp1 = new node;
	cin>>temp1->ti.d.month;
	cin>>temp1->ti.d.year;
	cin>>temp1->ti.d.day;
			
	cin>>temp1->ti.t.hrs;
	cin>>temp1->ti.t.minutes;
	cin>>temp1->ti.t.sec;
			
			
	cin>>temp1->da.owner_name;
	cin>>temp1->da.address;
	cin>>temp1->da.mobile_no;
	cin>>temp1->da.phone;
	cin>>temp1->da.value;
			
	
	if((*append_node)->reference_child_id==NULL)
	{
		temp1->reference_node_id=(*first_node); // giving address of parent node to child
		(*append_node)=temp1;
		temp1->node_number=++((*first_node)->node_number);
		temp1->child_id=(((*first_node)->child_id)++);
	}
	else
	{
		temp1->node_number= ++((*append_node)->node_number);
		temp1->child_id=(((*append_node)->child_id)++);
		(*append_node)->reference_child_id=temp1;    // this code append the node to the existing list (this covers 2 and 3 points)
		(*append_node)=temp1;
	}	
}
void make_multiset_first_node(node**root)
{
	int multisets=3; // suppose we want 3 multisets of first node
	int i=n;
	while(i--)
	{
		node*temp=*root;
		
		int size_set=2; // size of each set is 2
		int k=size_set;
		while(k--)
		{
			node*append_node;
			append_node->reference_child_id=NULL;
			append_fun(&append_node,root);
		}	
	}
	
}

int longest_chain_of_main_node(node**root)
{
	int count=0;
	while((*root)->reference_node_id!=NULL)
	{
		count++
	}
	return count;
}
	
int main()
{
	node*root; // root node is the first node
	root->reference_node_id=NULL; // reference node id of root node is nullas per your given format
	
	make_first_node(&root); // code of first part.
	
	make_multiset_first_node(&root);
	
	cout<<longest_chain_of_main_node(&root);

}
