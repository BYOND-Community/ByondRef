

 CSS attributes
----------------



 DM-CSS is a subset of CSS, and only supports some kinds of selectors and
attributes.




 The following table lists all supported attributes, and whether they are
supported in text output, maptext, and in other controls (labels/etc.) Other
controls will often allow only one style for an entire unit of text. A
checkbox in "Other" only indicates that
 *some* 
 support exists in other
controls, but it may vary by the type of control.



*some*






| 
 Attribute
  | 
 Output
  | 
 Maptext
  | 
 Other
  | 
 Notes
  |
| 
 color
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 Alpha colors may not be supported in some controls.
  |
| 
 background
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 In most cases, only applies to the entire text body.
  |
| 
 background-color
  | 
 ✔️
  | 
 ✔️
  |  |  |
| 
 background-image
  | 
 ✔️
  |  |  |  |
| 
 font
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-family
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-style
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-weight
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-size
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 text-decoration
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 Limited to
 
 underline
 
 ,
 
 overline
 
 ,
 
 line-through
 
 ,
 
 blink
 
 , and
 
 none
 
 . Support for each of these may vary depending on where they are used.
  |
| 
 text-align
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 justify
 
 is supported in output and maptext.
  |
| 
 vertical-align
  |  | 
 ✔️
  | 
 ✔️
  | 
 Limited to
 
 top
 
 ,
 
 middle
 
 , and
 
 bottom
 
 .
  |
| 
 text-indent
  | 
 ✔️
  | 
 ✔️
  |  |  |
| 
 margin-left
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 margin-right
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 margin-top
  |  |  | 
 ✔️
  |  |
| 
 margin-bottom
  |  |  | 
 ✔️
  |  |
| 
 margin
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 width
  | 
 ✔️
  | 
 ✔️
  |  | 
 Applies only to some elements such as images.
  |
| 
 height
  | 
 ✔️
  | 
 ✔️
  |  | 
 Applies only to some elements such as images.
  |
| 
 line-height
  | 
 ✔️
  | 
 ✔️
  |  | 
 Support in output control is limited; line heights less than 1 are not respected.
 
 Only unitless numbers, percentages, or em units are allowed.
  |
| 
 white-space
  | 
 ✔️
  | 
 ✔️
  |  | 
 normal
 
 ,
 
 nowrap
 
 ,
 
 pre
 
 ,
 
 pre-wrap
 
 ,
 
 pre-line
  |
| 
 text-shadow
  |  | 
 ✔️
  |  |  |
| 
 -dm-text-outline
  |  | 
 ✔️
  |  | 
 Custom attribute: Adds an outline to text. Values are in the form:
 
*width color style* 

 .
 
 The style is either blank, or any combination of the
 
 sharp
 
 and
 
 square
 
 keywords (see
 [Outline filter](#/{notes}/filters/outline) 
 ).
  |










| 
 Attribute
  | 
 Output
  | 
 Maptext
  | 
 Other
  | 
 Notes
  |

 
 Attribute
 |
 
 Output
 |
 
 Maptext
 |
 
 Other
 |
 
 Notes
 |
| 
 color
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 Alpha colors may not be supported in some controls.
  |

 
 color
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
 
 Alpha colors may not be supported in some controls.
 |
| 
 background
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 In most cases, only applies to the entire text body.
  |

 
 background
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
 
 In most cases, only applies to the entire text body.
 |
| 
 background-color
  | 
 ✔️
  | 
 ✔️
  |  |  |

 
 background-color
 |
 
 ✔️
 |
 
 ✔️
 |
  |
  |
| 
 background-image
  | 
 ✔️
  |  |  |  |

 
 background-image
 |
 
 ✔️
 |
  |
  |
  |
| 
 font
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |

 
 font
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
  |
| 
 font-family
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |

 
 font-family
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
  |
| 
 font-style
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |

 
 font-style
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
  |
| 
 font-weight
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |

 
 font-weight
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
  |
| 
 font-size
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |

 
 font-size
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
  |
| 
 text-decoration
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 Limited to
 
 underline
 
 ,
 
 overline
 
 ,
 
 line-through
 
 ,
 
 blink
 
 , and
 
 none
 
 . Support for each of these may vary depending on where they are used.
  |

 
 text-decoration
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
 
 Limited to
 
 underline
 
 ,
 
 overline
 
 ,
 
 line-through
 
 ,
 
 blink
 
 , and
 
 none
 
 . Support for each of these may vary depending on where they are used.
 |

 underline


 overline


 line-through


 blink


 none

| 
 text-align
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 justify
 
 is supported in output and maptext.
  |

 
 text-align
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
 
 justify
 
 is supported in output and maptext.
 |

 justify

| 
 vertical-align
  |  | 
 ✔️
  | 
 ✔️
  | 
 Limited to
 
 top
 
 ,
 
 middle
 
 , and
 
 bottom
 
 .
  |

 
 vertical-align
 |
  |
 
 ✔️
 |
 
 ✔️
 |
 
 Limited to
 
 top
 
 ,
 
 middle
 
 , and
 
 bottom
 
 .
 |

 top


 middle


 bottom

| 
 text-indent
  | 
 ✔️
  | 
 ✔️
  |  |  |

 
 text-indent
 |
 
 ✔️
 |
 
 ✔️
 |
  |
  |
| 
 margin-left
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |

 
 margin-left
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
  |
| 
 margin-right
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |

 
 margin-right
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
  |
| 
 margin-top
  |  |  | 
 ✔️
  |  |

 
 margin-top
 |
  |
  |
 
 ✔️
 |
  |
| 
 margin-bottom
  |  |  | 
 ✔️
  |  |

 
 margin-bottom
 |
  |
  |
 
 ✔️
 |
  |
| 
 margin
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |

 
 margin
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
  |
| 
 width
  | 
 ✔️
  | 
 ✔️
  |  | 
 Applies only to some elements such as images.
  |

 
 width
 |
 
 ✔️
 |
 
 ✔️
 |
  |
 
 Applies only to some elements such as images.
 |
| 
 height
  | 
 ✔️
  | 
 ✔️
  |  | 
 Applies only to some elements such as images.
  |

 
 height
 |
 
 ✔️
 |
 
 ✔️
 |
  |
 
 Applies only to some elements such as images.
 |
| 
 line-height
  | 
 ✔️
  | 
 ✔️
  |  | 
 Support in output control is limited; line heights less than 1 are not respected.
 
 Only unitless numbers, percentages, or em units are allowed.
  |

 
 line-height
 |
 
 ✔️
 |
 
 ✔️
 |
  |
 
 Support in output control is limited; line heights less than 1 are not respected.
 
 Only unitless numbers, percentages, or em units are allowed.
 |
  

| 
 white-space
  | 
 ✔️
  | 
 ✔️
  |  | 
 normal
 
 ,
 
 nowrap
 
 ,
 
 pre
 
 ,
 
 pre-wrap
 
 ,
 
 pre-line
  |

 
 white-space
 |
 
 ✔️
 |
 
 ✔️
 |
  |
 
 normal
 
 ,
 
 nowrap
 
 ,
 
 pre
 
 ,
 
 pre-wrap
 
 ,
 
 pre-line
  |

 normal


 nowrap


 pre


 pre-wrap


 pre-line

| 
 text-shadow
  |  | 
 ✔️
  |  |  |

 
 text-shadow
 |
  |
 
 ✔️
 |
  |
  |
| 
 -dm-text-outline
  |  | 
 ✔️
  |  | 
 Custom attribute: Adds an outline to text. Values are in the form:
 
*width color style* 

 .
 
 The style is either blank, or any combination of the
 
 sharp
 
 and
 
 square
 
 keywords (see
 [Outline filter](#/{notes}/filters/outline) 
 ).
  |

 
 -dm-text-outline
 |
  |
 
 ✔️
 |
  |
 
 Custom attribute: Adds an outline to text. Values are in the form:
 
*width color style* 

 .
 
 The style is either blank, or any combination of the
 
 sharp
 
 and
 
 square
 
 keywords (see
 [Outline filter](#/{notes}/filters/outline) 
 ).
 |

*width color style* 

*width color style*
  


 sharp


 square

[Outline filter](#/{notes}/filters/outline)

 These pseudo-classes are allowed in some contexts, but they can only change
the text color.









| 
 Psuedo-class
  | 
 Output
  | 
 Maptext
  | 
 Other
  | 
 Notes
  |
| 
 :link
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 :visited
  | 
 ✔️
  |  |  |  |
| 
 :active
  |  |  |  | 
 Currently not used, but future support is planned.
  |
| 
 :hover
  |  | 
 ✔️
  |  |  |










| 
 Psuedo-class
  | 
 Output
  | 
 Maptext
  | 
 Other
  | 
 Notes
  |

 
 Psuedo-class
 |
 
 Output
 |
 
 Maptext
 |
 
 Other
 |
 
 Notes
 |
| 
 :link
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |

 
 :link
 |
 
 ✔️
 |
 
 ✔️
 |
 
 ✔️
 |
  |
| 
 :visited
  | 
 ✔️
  |  |  |  |

 
 :visited
 |
 
 ✔️
 |
  |
  |
  |
| 
 :active
  |  |  |  | 
 Currently not used, but future support is planned.
  |

 
 :active
 |
  |
  |
  |
 
 Currently not used, but future support is planned.
 |
| 
 :hover
  |  | 
 ✔️
  |  |  |

 
 :hover
 |
  |
 
 ✔️
 |
  |
  |


---


