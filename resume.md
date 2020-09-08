---
YAML front matter
layout: page
title: Resume
permalink: /resume/
---

<!-- ## Resume -->
<!-- 
{/* <object data="https://drive.google.com/file/d/1xQTvctdQknnb4X_ZTIsDMAOIRCEvaV11/view?usp=sharing" type="application/pdf" width="750px" height="750px">
    <embed src="https://drive.google.com/file/d/1xQTvctdQknnb4X_ZTIsDMAOIRCEvaV11/view?usp=sharing" type="application/pdf">
        <p>This browser does not support PDFs. Please download the PDF to view it: <a href="https://drive.google.com/file/d/1xQTvctdQknnb4X_ZTIsDMAOIRCEvaV11/view?usp=sharing">Download PDF</a>.</p>
    </embed>
</object> --> */}

<script src="https://drive.google.com/file/d/1xQTvctdQknnb4X_ZTIsDMAOIRCEvaV11/view?usp=sharing"></script>

(async () => {
  const loadingTask = PDFJS.getDocument("/MyResume.pdf");
  const pdf = await loadingTask.promise;

  // Load information from the first page.
  const page = await pdf.getPage(1);

  const scale = 1;
  const viewport = page.getViewport(scale);

  // Apply page dimensions to the <canvas> element.
  const canvas = document.getElementById("pdf");
  const context = canvas.getContext("2d");
  canvas.height = viewport.height;
  canvas.width = viewport.width;

  // Render the page into the <canvas> element.
  const renderContext = {
    canvasContext: context,
    viewport: viewport
  };
  await page.render(renderContext);
  console.log("Page rendered!");
})();

<html>
<head>
  <meta charset="UTF-8">
  <title>My Resume</title>
  <script src="/pdf.js"></script>
  <script src="/simple.js"></script>
</head>
<body>
  <canvas id="pdf"></canvas>
</body>
</html>