---
Factions: 
Genre: 
Race: 
Age: 
Archétype:
---
<% tp.file.title %>
<% await tp.file.move("publish/Ressources/PNJ/" + tp.file.title) %>
<%*
const hasTitle = !tp.file.title.startsWith('NewNPC');
let title;
if (!hasTitle) {
	title = await tp.system.prompt('Nom du PNJ');
	await tp.file.rename(title);
} else {
	title = tp.file.title;
}
%>