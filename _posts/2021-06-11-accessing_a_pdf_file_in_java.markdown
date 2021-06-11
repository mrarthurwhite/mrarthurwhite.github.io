---
layout: post
title:      "Accessing a PDF file in Java"
date:       2021-06-11 18:24:36 +0000
permalink:  accessing_a_pdf_file_in_java
---

So I have done extensive PDF file manipulation using 3rd party libraries that access pdf files.
I reviewed the code I had written & it is extensive & elaborate so I cannot come up with a straightforward example (unfortunately). This violates my own principles of presenting minimal , atomic examples but this should demonstrate how convoluted & uneasy & un - developer friendly some libraries (even commercial 3rd party libraries) are. 

The following requires a jar file and the code opens, reads & outputs the first page of a pdf file to a text file.

[link to git hub source ](https://github.com/mrarthurwhite/ReadPDF)

```
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileOutputStream;
import java.io.OutputStreamWriter;
import com.snowtide.PDF;
import com.snowtide.pdf.Document;
import com.snowtide.pdf.OutputTarget;
import com.snowtide.pdf.Page;
/**
 * @author SOLON
 * 1. add pdfxstream.jar 
 * 2. add the jar file to the classpath/build path
 * 3. then read the pdf file specifying the file name (here "hello.pdf")
 * 4. then specify an output file name (here hello.txt)
 * 5. close the pipes and writers
 *
 */
public class ReadPDF {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		String pdf_filename="hello.pdf";
		File pdfFile= new File(pdf_filename);  // The PDF file from where you would like to extract
		Document pdf = PDF.open(pdfFile);
		File txtFile = new File("hello.txt");
	    Page page = pdf.getPage(0); // access just the first page
		try {
			BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(new FileOutputStream(txtFile)));
		    page.pipe(new OutputTarget(writer));
		    pdf.close();
		    writer.flush();
		    writer.close();
		} catch (Exception e) {
			e.printStackTrace();
		}


	}

}
```

As the reader may see it is not easy to understand what is going which is not in line with higher level languages that an OO language like Java purports to be.

Why don't we write in Assembly language ? because it is arcane and requires too many lines of code. 
Why do we prefer higher level languages like Java/Ruby/ Perl/ C++/ Javascript ? because they are supposed to be akin to pseudo code requiring the least amount of configuration (recall ROR's motto of "less configuration, more convention" & JS which is forgiving & easy to use with multiple overloaded methods , thereby requiring lesser configuration). We gravitate to higher level languages because they are *accessible* & readable & human friendly & even developer friendly.

Again the idea is to make configuration *optional* as opposed to mandatory for even the most basic tasks. Anyone who has worked with Spring, hibernate (an ORM) or any other java framework would know what I am saying about configuration (just installing IDEs & JDKs used to take entire weekends with classpath conflicts etc.).

I wanted to just print out the text from a pdf file but the docs were not there, the tutorials were not there & from the looks of it even after working with the  `snowtide` library extensively I had forgotten precisely how to do that. I searched my code & I could not find the initial hello-word examples so this is the best I could come up with after great unease (because even the introductory documents are not helpful).



