# FACTORY METHOD

1. What is Factory method?

```
Provide an interface for creating object in a superclass
```

2. Solution

```
- Replace direct object constructor calls (`new` operator) with calls to a special factory method.

- Object returned by a factory method are often referred to as product
```

3. Implement a factory method

- Typescript

```ts
interface Reports {
	generate(): string;
}

class PDFReport implements Reports {
	generate(): string {
		return 'Generate PDF report';
	}
}

class HTMLReport implements Reports {
	generate(): string {
		return 'Generate HTML report';
	}
}

interface ReportFactory {
	createReport(): Report;
}

class PDFReportFactory {
	createReport(): Reports {
		return new PDFReport();
	}
}

class HTMLReportFactory {
	createReport(): Reports {
		return new HTMLReport();
	}
}

// usage
const pdfReportFactory = new PDFReportFactory();
const pdfReport = pdfReportFactory.createReport();
console.log(pdfReport.generate());

const htmlReportFactory = new PDFReportFactory();
const htmlReport = htmlReportFactory.createReport();
console.log(htmlReport.generate());
```
