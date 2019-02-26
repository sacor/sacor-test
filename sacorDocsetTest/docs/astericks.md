 If you specify a conversation handle, only events associated with the associated conversation endpoint are reported. If you specify a conversation ID, all events for that conversation and its initiator and target endpoints are reported. If a conversation group ID is specified, all events for all conversations and endpoints in the conversation group are reported.  
  
 *conversation_handle*  
 A unique identifier that identifies a conversation endpoint in an application. Conversation handles are unique to one endpoint of a conversation, the initiator and target endpoints have separate conversation handles.  
  
 Conversation handles are returned to applications by the *@dialog_handle* parameter of the **BEGIN DIALOG** statement, and the **conversation_handle** column in the result set of a **RECEIVE** statement.  
  
 Conversation handles are reported in the **conversation_handle** column of the **sys.transmission_queue** and **sys.conversation_endpoints** catalog views.  
  
 *conversation_group_id*  
 The unique identifier that identifies a conversation group.  
  
 Conversation group IDs are returned to applications by the *@conversation_group_id* parameter of the **GET CONVERSATION GROUP** statement and the **conversation_group_id** column in the result set of a **RECEIVE** statement.  
  
 Conversation group IDs are reported in the **conversation_group_id** columns of the **sys.conversation_groups** and **sys.conversation_endpoints** catalog views.  
  
 *conversation_id*  
 The unique identifier that identifies a conversation. Conversation IDs are the same for both the initiator and target endpoints of a conversation.  
  
 Conversation IDs are reported in the **conversation_id** column of the **sys.conversation_endpoints** catalog view.  
  