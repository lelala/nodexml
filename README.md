nodexml
=======

Parse xml to json object and json object to xml.
Support element innertext, attribute, cdata section.

//parse xml to object
var xmlobj = require('nodexml').xml2obj("<test>aaa</test>");
//xmlobj = { test : "aaa" }

//parse object to xml
var xmlstring = require('nodexml').obj2xml({ test: "test" },"root");//the second param is root element name
//xmlstring = "<root><test>test</test></root>"

This module keeps xml and object in the same structure.Sometimes structures are not clearly, developers should normalize it.
Ex: 
<dogs><dog name="bobo"></dog><dog name="dodo"></dog></dogs> => {dogs:{dog:[{name:"bobo"},{name:"dodo"}]}}
<dogs><dog name="bobo"></dog></dogs> => {dogs:{dog:{name:"bobo"}}}

If dog is multiple, structure will be array.If is single, structure will be single object.
Use dogs.dog = [].concat(dogs.dog) to ensure dog is an array.

Demo:
https://docs.google.com/a/ischool.com.tw/file/d/0B6dPaNMUqN32NDY4ODNkYVhDWFU/edit?usp=drive_web
