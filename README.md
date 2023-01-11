# HTML-CSS
package com.example.Dpf;
import com.aspose.pdf.License;
import com.aspose.pdf.AbsorbedCell;
import com.aspose.pdf.AbsorbedRow;
import com.aspose.pdf.AbsorbedTable;
import com.aspose.pdf.Document;
import com.aspose.pdf.TableAbsorber;
import com.aspose.pdf.TextFragmentCollection;

import java.io.File;

public class DpfApplication {

	public static void main(String[] args) throws Exception { // main function for reading PDF table data in ReadPDFTableInJava

		// For avoiding the trial version limitation, load the Aspose.PDF license prior to reading table data
//		License licenseForHtmlToPdf = new License();
//		licenseForHtmlToPdf.setLicense("Aspose.Pdf.lic");

		// Load a source PDF document which contains a table in it
		Document pdfDocument = new Document("C:\\Users\\Бонпари\\Desktop\\e69c0ceb-4044-4b12-919b-e38bf2386716.pdf");
//		Document pdfDocument = new Document("PdfWithTable.pdf");

		// Instantiate the TableAbsorber object for PDF tables extraction
		TableAbsorber tableAbsorber = new TableAbsorber();

		// visit the table collection in the input PDF
		tableAbsorber.visit(pdfDocument.getPages().getUnrestricted(63));

		// Access the desired table from the tables collection
		AbsorbedTable absorbedTable = tableAbsorber.getTableList().get(0);

		int count=0;
		// Parse all the rows and get each row using the AbsorbedRow
		for (AbsorbedRow pdfTableRow : absorbedTable.getRowList())
		{
			// Access each cell in the cells collection using AbsorbedCell
			for (AbsorbedCell pdfTableCell : pdfTableRow.getCellList())
			{
				// Access each text fragment from the cell
				TextFragmentCollection textFragmentCollection = pdfTableCell.getTextFragments();

				// Access each text fragment from the fragments collection
				for (com.aspose.pdf.TextFragment textFragment : textFragmentCollection)
				{
					// Display the table cell text
					System.out.print(textFragment.getText() + " ");
				}
			}
			count++;
			System.out.println("");
		}

		System.out.println("Done + " + count);
		System.out.println(pdfDocument.getPages().size());
	}

}
