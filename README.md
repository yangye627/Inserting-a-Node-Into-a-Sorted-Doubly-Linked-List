DoublyLinkedListNode* sortedInsert(DoublyLinkedListNode* llist, int data) {

    DoublyLinkedListNode *ptr = new DoublyLinkedListNode(data);
    DoublyLinkedListNode *mptr = llist;
    if(llist == nullptr){
        return llist;
    }
    //check if insert at the begin
    else if (mptr->data > ptr->data){
        ptr->next = mptr;
        mptr->prev = ptr;
        return ptr;
    }
    else{
		//move mptr to the node that is 1st num > data
        while(mptr->data < ptr->data){
	    //check if insert at the end
            if(mptr->next == nullptr){
                mptr->next = ptr;
                ptr->prev = mptr;
                return llist;
            }
            else{
                mptr = mptr->next;
            }
        } 
	//otherwise
        DoublyLinkedListNode *temp = mptr->prev;
        temp->next = ptr;
        ptr->next = mptr;
        mptr->prev = ptr;
        ptr->prev = temp;
    }

    return llist;
}
