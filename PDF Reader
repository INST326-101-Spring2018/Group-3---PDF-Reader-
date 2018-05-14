import PyPDF2

#rotate section by Brady

def rotate(fileName, newName, angle):
    fin= open(fileName, 'rb')
    reader= PyPDF2.PdfFileReader(fin)
    writer=PyPDF2.PdfFileWriter()
    #loop for rotating each page
    for page in range(reader.numPages):
        pageObj = reader.getPage(page)
        pageObj.rotateClockwise(angle)
        writer.addPage(pageObj)
        #creating new place to save pdf
    newFile = open(newName, 'wb')
    writer.write(newFile)
    fin.close()
    newFile.close()
def rotate_main():
    #main function for names of files and how much to rotate
    openName=input("What is the name of the file you want to open? ")
    name2=input("what do you want to name the file after rotating it? ")
    degrees=input("How many degrees do you want to rotate it clockwise?: ")
    degrees=int(degrees)
    rotate(openName, name2, degrees)
    print("Your PDF has now been rotated " + str(degrees) + " degrees and saved as " + str(name2))

#watermark section by Brady

def add_watermark(watermark_file, pageObject):
    watermark_file_Object = open(watermark_file, 'rb')
    reader=PyPDF2.PdfFileReader(watermark_file_Object)
    # merging watermark with the passed page from loop
    pageObject.mergePage(reader.getPage(0))
    watermark_file_Object.close()
    return pageObject

def watermark_main():
    watermark_name = input("What is the file name of your watermark? ")
    no_Watermark_name = input("What is the name of the file you want to add the watermark to?")
    complete_Pdf = input("What do you want to name the new PDF with the watermark?")

    pdfObject = open(no_Watermark_name, 'rb')
    reader = PyPDF2.PdfFileReader(pdfObject)
    writer = PyPDF2.PdfFileWriter()

    # loop for watermark on each page
    for page in range(0, reader.numPages):
        watermark_Obj=add_watermark(watermark_name, reader.getPage(page))
        writer.addPage(watermark_Obj)

    # saving and closing files
    complete = open(complete_Pdf, 'wb')
    writer.write(complete)
    pdfObject.close()
    complete.close()
    print("Your pdf has now had the watermark applied to it and is now saved as " + str(complete_Pdf))

#melody dastanlee PDF merger

class Merge:
    def merge(pdfs,output):
        Merger = PyPDF2.PdfFileMerger()
        for pdf in pdfs:
            Merger.append(pdf)
            # writing combined pdf to output pdf file
        with open(output, 'wb') as f:
            Merger.write(f)
    def merger_main():
        # pdf files to merge
        pdf_1 = input("What is the name of the first pdf you want to open? ")
        pdf_2 = input("What is the name of the file you want to merge with the other? ")
        pdfs = [pdf_1, pdf_2]

        # output pdf file name
        output = input("What do you want to save the merged pdf as? ")

        # calling pdf merge function
        merge(pdfs, output)
        print("Your pdfs have now been merged and saved as " + str(output))

# splitting one PDF into separate one-page PDFs by Layla
def pdf_splitter_main():
    from PyPDF2 import PdfFileWriter, PdfFileReader
    file_name= input("What is the name of the pdf you want to split? ")
    infile = PdfFileReader (open(file_name, 'rb'))
    original_file_name = file_name.split('.')

    for i in range(infile.getNumPages()):
        p = infile.getPage(i)
        outfile = PdfFileWriter()
        outfile.addPage(p)
        with open(original_file_name[0] + ' page-%02d.pdf' % i, 'wb') as f:
            outfile.write(f)
    print("The PDF has now been split and saved as multiple files")

#text extractor by Shivani
def text_extractor_main():
    file_name=input("What is the name of the PDF you want to extract text from? ")
    txt_name=input("What do you want to name the extracted text file? (please end the name with '.txt') ")
    pdf_file = open(file_name, 'rb')
    pdf_outfile = open(txt_name,'w')
    pdfReader = PyPDF2.PdfFileReader(pdf_file)
    #reads through each page one by one getting the text and saving it to a file
    for i in range(pdfReader.getNumPages()):
        page=pdfReader.getPage(i)
        text=page.extractText()
        pdf_outfile.write(text)
    pdf_file.close()
    pdf_outfile.close()
    print("Your text has been extracted and saved as " + str(txt_name))

def main():
    print("Welcome to the pdf Manager!")
    print("1: PDF Rotate")
    print("2: PDF Watermark")
    print("3: PDF Merger")
    print("4: PDF Splitter")
    print("5: PDF Text Extractor")
    choice = input("Which function would you like to do 1-5?")
    choice= int(choice)
    if choice ==1:
        rotate_main()
    elif choice==2:
        watermark_main()
    elif choice==3:
        merger_main()
    elif choice ==4:
        pdf_splitter_main()
    elif choice ==5:
        text_extractor_main()
main()
