[[Android]]

- RecyclerView is a ViewGroup
-  It is a successor of the **GridView** and **ListView**.
-  Improvement is achieved by recycling the views which are out of the visibility of the user

each element in the group is called viewholder
each element donot have any data 
recycler view bind data to it by calling methods present in adapter(which we create)
layout manager arranges the elements

(Your view holder is a wrapper around a View, and that view is managed by RecyclerView.

The Adapter creates ViewHolder objects as needed and also sets the data for those views. The process of associating views to their data is called binding.)



#inflater 
Think of an "inflater" as a tool that takes a blueprint (XML layout file) and turns it into an actual object in memory.

• What is the difference between ListView and RecyclerView?  
• How would you improve RecyclerView's scrolling performance?  
• How does RecyclerView work internally?  
• How do you handle multiple view types in a single RecyclerView?  
• What is DiffUtil, and how does it improve RecyclerView performance?  
• What is the purpose of RecyclerView.setHasFixedSize(true)?  
• Explain the roles of RecyclerView.Adapter and RecyclerView.ViewHolder.  
• How do you update a specific item in a RecyclerView?  
• What are the main components of a RecyclerView?  
• How does RecyclerView improve performance compared to ListView?
