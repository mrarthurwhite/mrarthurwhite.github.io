---
layout: post
title:      "Serializing & Deserializing A Class in Java"
date:       2021-06-08 12:39:15 +0000
permalink:  serializing_and_deserializing_a_class_in_java
---


Following is a very straightforward and minimal example of how to serialize & deserialize a class in Java. 
The class we will serialize & deserialize to and from XML is a `Contacts` class that has a `map` of emails & names associated with the emails. 

```
/**
 * 
 */
import javax.xml.bind.annotation.XmlRootElement;

import java.util.LinkedHashMap;

/**
 *
 */
@XmlRootElement (name="contacts")

public class Contacts {

	private  LinkedHashMap<String, String> map = new LinkedHashMap<String, String>();
	public LinkedHashMap<String, String> getMap() {
		return map;
	}


	public void setMap(LinkedHashMap<String, String> map) {
		this.map = map;
	}
	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}

}

```

The class where we will be serializing and deserializing from first creates the contacts so : 

```
		Contacts cmap = new Contacts();
		cmap.getMap().put("mr.arthur.white@gmail.com", "Arthur White");
		cmap.getMap().put("arthur.uthersonn@gmail.com", "Arthur Uthersonn");
```

Then it seriealizes the maps so: 
```
		SerializeToXML sxml = new SerializeToXML();
		sxml.serialize(cmap,outputContactsFile);
		
			private void serialize(Contacts map, String xmlFile ) {
		try {
			JAXBContext jxbCntxt = JAXBContext.newInstance(Contacts.class);
			Marshaller marshaller = jxbCntxt.createMarshaller();
			marshaller.setProperty(Marshaller.JAXB_FORMATTED_OUTPUT, true);
			// output file to console
			marshaller.marshal(map, System.out);
			// save to xml file
			marshaller.marshal(map, new File(xmlFile));
		} catch (Exception e) {
			e.printStackTrace();
		}		
	}
		
```

And it deserializes it so :

```
		sxml.deSerialize(outputContactsFile);// deserealize the map

	private void deSerialize(String xmlFile ) {
		try {
			JAXBContext jxbCntxt = JAXBContext.newInstance(Contacts.class);
			Unmarshaller unmarshaller = jxbCntxt.createUnmarshaller();
			Contacts cmap= (Contacts) unmarshaller.unmarshal(new File(xmlFile));
			System.out.println("Number of contacts :  " + cmap.getMap().size());
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
```

The output of the above is as follows : 
```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<contacts>
    <map>
        <entry>
            <key>mr.arthur.white@gmail.com</key>
            <value>Arthur White</value>
        </entry>
        <entry>
            <key>arthur.uthersonn@gmail.com</key>
            <value>Arthur Uthersonn</value>
        </entry>
    </map>
</contacts>
Number of contacts :  2
```

And ofcourse the source repository is [this](https://github.com/mrarthurwhite/java_serialize_deserialize_class).
