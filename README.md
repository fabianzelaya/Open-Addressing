### Object Oriented Programming and Data Structures - 2022

# Open Addressing
In the preceding sections, you studied a hash table implementation that uses separate chaining for collision handling, placing all elements with the same hash code in a bucket. This implementation is fast and easy to understand, but it requires storage for the links to the nodes. If one places the elements directly into the hash table, then one doesn’t need to store any links. This alternative technique is called open addressing. It can be beneficial if one must minimize the memory usage of a hash table.

Of course, open addressing makes collision handling more complicated. If you have two elements with (compressed) hash code h, and the first one is placed at index h, then the second must be placed in another location.

There are different techniques for placing colliding elements. The simplest is linear probing. If possible, place the colliding element at index h + 1. If that slot is occupied, `try h + 2, h + 3`, and so on, wrapping around to `0, 1, 2`, and so on, if necessary. This sequence of index values is called the probing sequence. (You can see other probing sequences in Programming Project _TARGET-UNUSED_ and Programming Project _TARGET-UNUSED_.) If the probing sequence contains no empty slots, one must reallocate to a larger table.

How do we find an element in such a hash table? We compute the hash code and traverse the probing sequence until we either find a match or an empty slot. As long as the hash table is not too full, this is still an O(1) operation, but it may require more comparisons than with separate chaining. With separate chaining, we only compare objects with the same hash code. With open addressing, there may be some objects with different hash codes that happen to lie on the probing sequence.

![embedded_image_1_5dc30a77-2314-462e-8d5f-415c18f7947d_gLEmHdKeSJuy88WSNx0e](https://user-images.githubusercontent.com/71942518/189571574-3ad198c3-5497-4190-ac6a-2188a865138e.png)

Adding an element is similar. Try finding the element first. If it is not present, add it in the first empty slot in the probing sequence.

Removing an element is trickier. You cannot simply empty the slot at which you find the element. Instead, you must traverse the probing sequence, look for the last element with the same hash code, and move that element into the slot of the removed element. Then rehash all elements that follow until you reach an empty slot (Programming Project TARGET-UNUSED).

![embedded_image_1_6141df22-7139-4bf3-b449-12bc97458582_gLEmHdKeSJuy88WSNx0e](https://user-images.githubusercontent.com/71942518/189571616-49db9305-4b0f-4e57-a37a-191c147e29eb.png)

Alternatively, you can replace the removed element with a special “inactive” marker that, unlike an empty slot, does not indicate the end of a probing sequence. When adding another element, you can overwrite an inactive slot (Programming Project TARGET-UNUSED).


## Thanks for watching!

If you liked my coding then follow me on my [Instagram](https://www.instagram.com/fabianzelayahn/) account or [GitHub](https://github.com/fabianzelaya) account.

<img src="https://ucarecdn.com/d1a85e63-35f9-41d7-b758-ff05742057d1/GitHub_Black_Signature.png" width="240" height="79.63" />
