# Inserting-a-Node-Into-a-Sorted-Doubly-Linked-List

DoublyLinkedListNode* sortedInsert(DoublyLinkedListNode* llist, int data) {
    DoublyLinkedListNode *ptr = new DoublyLinkedListNode(data);
    DoublyLinkedListNode *mptr = llist;
    if(llist == nullptr){
        return llist;
    }
    else if (mptr->data > ptr->data){
        ptr->next = mptr;
        mptr->prev = ptr;
        return ptr;
    }
    else{
        while(mptr->data < ptr->data){
            if(mptr->next == nullptr){
                mptr->next = ptr;
                ptr->prev = mptr;
                return llist;
            }
            else{
                mptr = mptr->next;

            }
        }      
        DoublyLinkedListNode *temp = mptr->prev;
        temp->next = ptr;
        ptr->next = mptr;
        mptr->prev = ptr;
        ptr->prev = temp;
    }

    return llist;
}
