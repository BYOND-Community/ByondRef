

 tags (text)
-------------




**See also:** 


[entities (text)](#/DM/text/entities) 

[macros (text)](#/DM/text/macros) 

[style sheets](#/DM/text/style) 

[text](#/DM/text) 






**See also:** 

**See also:**

[entities (text)](#/DM/text/entities) 

[macros (text)](#/DM/text/macros) 

[style sheets](#/DM/text/style) 

[text](#/DM/text) 




[entities (text)](#/DM/text/entities)

[macros (text)](#/DM/text/macros) 

[style sheets](#/DM/text/style) 

[text](#/DM/text) 



[macros (text)](#/DM/text/macros)

[style sheets](#/DM/text/style) 

[text](#/DM/text) 


[style sheets](#/DM/text/style)

[text](#/DM/text) 

[text](#/DM/text)

 Text tags (also known as
 *elements* 
 by snooty HTML purists) control
how the text is formatted. HTML syntax is used, so all tags start with
 `<` 
 and end with
 `>` 
 . The tags which are
currently supported by Dream Seeker, are listed below:



*elements*
`<`
`>`

```
<A></A>              // anchor (hyperlink)
<ACRONYM></ACRONYM>  // acronym or abbreviation
<B></B>              // bold text
<BIG></BIG>          // one size bigger text
<BODY></BODY>        // body of html document
<BR>                 // line break
<CITE></CITE>        // citation reference
<CODE></CODE>        // program source code
<DFN></DFN>          // definition
<DIV></DIV>          // used in conjunction with style sheets
<EM></EM>            // emphasized text
<FONT></FONT>        // font face, color, and size
<H1></H1>            // heading level
<H2></H2>
<H3></H3>
<H4></H4>
<H5></H5>
<H6></H6>
<HEAD></HEAD>        // document head section
<HTML></HTML>        // html document
<I></I>              // italic text
<IMG></IMG>          // display icons
<KBD></KBD>          // keyboard input
<P></P>              // paragraph
<PRE></PRE>          // pre-formatted text
<S></S>              // overstrike text
<SAMP></SAMP>        // sample output
<SMALL></SMALL>      // one size smaller text
<SPAN></SPAN>        // used in conjunction with style sheets
<STRONG></STRONG>    // strongly emphasized text
<STYLE></STYLE>      // contains a style sheet
<TITLE></TITLE>      // document title
<TT></TT>            // typewriter style
<U></U>              // underline
<VAR></VAR>          // variable name
<XMP></XMP>          // preformatted (tags ignored)

```


 In addition to these, the
 `<BEEP>` 
 tag, which is not
standard HTML, may be used to beep the terminal.



`<BEEP>`

 Some tags take additional parameters, known as attributes. The most common
ones are
 `<FONT>` 
 and
 `<A>` 
 .
The syntax for these is illustrated by the following two examples:



`<FONT>`
`<A>`

 "How about
 
 this
 
 !"
"Click
 [here](byond.com "BYOND!") 
 !"


 this

[here](byond.com "BYOND!")

 As many attributes may be specified as desired. The attribute value may
have quotes around it, but this is only necessary if the value contains
spaces. It is usually more convenient to use single quotes so you don't have
to escape the double quotes, but you can also embed the HTML in a
 [text document](#/DM/text) 
 to avoid the need for escaping quotes.



[text document](#/DM/text)

 When applying color to text, you can use hexadecimal RGB or you can use
one of the named
 [HTML colors](#/{{appendix}}/html-colors) 
 .



[HTML colors](#/{{appendix}}/html-colors)

 Text sizes range from 1 to 7, 1 being the smallest and 7 being the largest.
In addition to absolute sizes, relative sizes may be specified (like +1 for
one size bigger or -1 for one size smaller).





---


