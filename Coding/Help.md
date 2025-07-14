
# Best Practice of Passing Data from Custom Component to Form Actions
I'm using the Calendar component of svelte shadcn and I'm wondering how will I pass this data to form actions?

I asked ChatGPT and it gave me answers:

1. Use hidden <input\> elements that are binded to the same value as the Calendar binding. But I don't think if this is a good practice though, it seems weird and unusual but hey it works. Unfortunately, there's a problem into it, because not only that it is a single data variable, it is a date in an object that contains other fields as well. So I don't know how to work around this.
2. 

---
