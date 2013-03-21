#include<stdio.h>
#include<stdlib.h>


//Global Varilables
char *data;
int flag = 0;


// Four Tree Structure!
struct FourTree
{
	char color;
	struct FourTree *child[4];
};
typedef struct FourTree FourTree;
FourTree *t3;


// To initialize children to null if a node has no children
void createNoChild(FourTree *ptr)
{
	int i;
	for(i=0;i<4;i++)
		ptr->child[i] = NULL;
}

// Get the character from Input supplied
char getNextColor()
{
	if(data !=NULL)
	{
		return(*data++);
	}	
	else
	{
		printf("Error in data!");
		exit(1);
	}	
}


// Recursive function to create a 4Tree
FourTree* create4tree()
{
	char c;
	int i;
	int retval;
	FourTree *root = (FourTree *)malloc(sizeof(FourTree));

	c = getNextColor();
	switch(c)
	{
		case 'B' :
		case 'b' : 
		{
			root->color = 'B';
			createNoChild(root);
			break;
		} 
		case 'W' :
		case 'w' :
		{
			root->color = 'W';
			createNoChild(root);
			break;
		}
		case 'M' :
		case 'm' :
		{
			root->color = 'M';
			for(i=0;i<4;i++)
			{
				if((root->child[i] = create4tree()) == NULL)
				{
					printf("Error");
				}
			}	
			break;
		}
		default :
		{
			printf("\nInvalid input!  exiting...\n");
			exit(1);				
			break;
		}
	}
	return root;			
} 


// To display a 4Tree
void display4tree(FourTree *root)
{
	int i;
	if(root == NULL)
	{
		return;
	}
	printf("%c",root->color);
	if(root->color == 'M')
	{
		for(i=0;i<4;i++)
			display4tree(root->child[i]);
	}
}


char DFStraversal(FourTree *t)
{	
	char c;
	int i;
	// t cannot be NULL
	
	// The interesting thing here to NOTE is that any of the child node of t is white then the result will be white
	// This makes our task easier and we do not have to traverse whole tree, we can just traverse the tree until we get one white node
	
	// flag is globally defined and initially starts with zero
	
	for(i=0;i<4;i++)
	{
		if(flag == 1)
			return c;
		
		if( (t->child[i])->color == 'W')
		{
			c = 'W';
			flag = 1;
			return c;
		}
		if( (t->child[i])->color == 'B')
		{
			c = 'B';
		}
		if( (t->child[i])->color == 'M')
		{
			c = DFStraversal(t->child[i]);
		}
	}

	return c;
}


// Resursive function to Merge two 4Trees
FourTree* merge(FourTree *t1, FourTree *t2)
{
	int i;
	char color;	
	
	if(t1 == NULL || t2 == NULL)
		return NULL;

	//FourTree *root = (FourTree*) malloc (sizeof(FourTree));

	if(t1->color == t2->color)
	{
		if(t1->color == 'B' || t1->color == 'W')
		{
			FourTree *root = (FourTree*) malloc (sizeof(FourTree));
			root->color = t1->color;
			createNoChild(root);
			return root;
		}
	}
	
	if( (t1->color == 'W' && t2->color == 'B') || (t1->color =='B' && t2->color == 'W') )
	{
		FourTree *root = (FourTree*) malloc (sizeof(FourTree));
		root->color = 'W';
		createNoChild(root);
		return root;
	}
		
	if( t1->color == 'M' && t2->color == 'M' )
	{
		FourTree *root = (FourTree*) malloc (sizeof(FourTree));
		root->color = 'M';
		for(i=0;i<4;i++)
		{
			root->child[i] = merge(t1->child[i],t2->child[i]);
		}		
		return root;
	} 	

	if( t1->color == 'M' && (t2->color == 'B' || t2->color == 'W') )
	{
		FourTree *root = (FourTree*) malloc (sizeof(FourTree));
		
		// if t2 is white then any way answer is going to be white so no need to check for children of t1		
		if(t2->color == 'W')
		{
			root->color = 'W';
			createNoChild(root);	
			return root;	
		}

		
		color = DFStraversal(t1);	
	
		if(color == 'W')
		{
			root->color = 'W';
		}
		else
		{
			root->color = t2->color;
		} 
		createNoChild(root);
		return root;
	}

	if( t2->color == 'M' && (t1->color == 'B' || t1->color == 'W') )
	{
		FourTree *root = (FourTree*) malloc (sizeof(FourTree));

		// if t1 is white then any way answer is going to be white so no need to check for children of t2		
		if(t1->color == 'W')
		{
			root->color = 'W';	
			createNoChild(root);
			return root;	
		}

		color = DFStraversal(t2);
		if(color == 'W')
		{
			root->color = 'W';
		}
		else
		{
			root->color = t1->color;
		} 
		createNoChild(root);
		return root;
	}
}


int main(int argc, char *argv[])
{
	
	if(argc != 3)
	{
		printf("Usage : ./tree 4Tree1 4Tree2 \nNote : Here 4Tree1 and 4Tree2 are Depth First Traversal of corresponding trees!\n");
		exit(0);
	}	

	FourTree *tree1,*tree2;
	FourTree *MergedTree;
	

	// Create first 4Tree
	//printf("\nCreating 4Tree1!");
	data = argv[1];
	if( (tree1 = create4tree()) == NULL )
	{
		printf("Error!");
	}
	if(*data != '\0')
	{
		printf("\nInvalid input 1!  exiting..\n");
		exit(0);
	}	
	
	// Display first 4Tree
	printf("\nDisplaying 4Tree 1! \n");
	display4tree(tree1);
	printf("\n");


	// Create second 4tree
	//printf("\nCreating 4Tree2!");
	data = argv[2];
	if( (tree2 = create4tree(tree2)) == NULL )
	{
		printf("Error!");
	}
	if( *data != '\0')
	{
		printf("\nInvalid input 2!  exiting..\n");
		exit(0);
	}
	// Display second 4Tree
	printf("\nDisplaying  4Tree 2! \n");
	display4tree(tree2);
	printf("\n");

	if( (MergedTree = merge(tree1,tree2)) == NULL )
	{
		printf("Merge error!");
	}

	// Display Merged 4Tree
	printf("\nDisplaying  Merged 4Tree! \n");
	display4tree(MergedTree);
	printf("\n\n");
	return 0;
}
