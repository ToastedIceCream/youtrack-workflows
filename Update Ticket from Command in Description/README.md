Update Ticket from Command in Description 
====================================================
When ticket is first created, parse the Description and apply Command if command syntax is found
 

when issue.becomesReported() { 
   
  var syntaxStart = "__inDescCmdStart__"; 
  var syntaxEnd = "__inDescCmdEnd__"; 
   
  var index = issue.description.indexOf(syntaxStart, opts); 
  if (index != -1) { 
    var value = issue.description.substring(index + (syntaxStart).length); 
    index = value.indexOf(syntaxEnd, opts); 
    if (index != -1) { 
      value = value.substring(0, index); 
      if (value.isNotEmpty) { 
        issue.applyCommand(value); 
      } 
    } 
  } 
}
