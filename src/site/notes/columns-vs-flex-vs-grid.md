---
{"dg-publish":true,"permalink":"/columns-vs-flex-vs-grid/","tags":["dev"]}
---


- Columns
	- Allows variable height rows and don't need a fixed height to 'wrap'
- Flex
	- Allows items to grow or shrink but needs a fixed width or height to 'wrap'
	- Rows adjust to the height of all items so they're always aligned
	- Can't align items along the main axis, can only provide a general rule like 'justify evenly'.
		- E.g. can't say move this one item to the end.
- Grid
	- Is very powerful but the more verbose and the main constraint is that items must align with a row or column track
	- Can't have both automatic columns and rows, one or the other must be specified