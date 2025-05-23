<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Krishikosh Thesis Downloader</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter :wght@400;600;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Inter', sans-serif;
      background-color: #f4f7fa;
      color: #333;
      margin: 0;
      padding: 0;
    }

    .container {
      max-width: 600px;
      margin: 50px auto;
      background: white;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.08);
    }

    h1 {
      font-size: 28px;
      color: #2c3e50;
      margin-bottom: 5px;
    }

    h2 {
      font-size: 16px;
      font-weight: normal;
      color: #777;
      margin-top: 0;
    }

    p {
      font-size: 15px;
      color: #555;
      margin-bottom: 20px;
    }

    input[type="text"] {
      width: 100%;
      padding: 12px;
      font-size: 15px;
      border: 1px solid #ccc;
      border-radius: 6px;
      box-sizing: border-box;
      margin-top: 10px;
    }

    button {
      background-color: #3498db;
      color: white;
      padding: 12px 20px;
      font-size: 15px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      margin-top: 10px;
      transition: background 0.3s ease;
    }

    button:hover {
      background-color: #2980b9;
    }

    .result {
      margin-top: 20px;
      padding: 15px;
      border-radius: 6px;
      font-size: 15px;
    }

    .success {
      background-color: #d4edda;
      color: #155724;
      border-left: 4px solid #28a745;
    }

    .error {
      background-color: #f8d7da;
      color: #721c24;
      border-left: 4px solid #dc3545;
    }

    a {
      display: inline-block;
      margin-top: 8px;
      color: #3498db;
      text-decoration: none;
      font-weight: 600;
    }

    a:hover {
      text-decoration: underline;
    }

    .slogan {
      font-size: 16px;
      font-style: italic;
      color: #aaa;
      margin-top: 10px;
      display: block;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Krishikosh Thesis Downloader</h1>
    <h2>by Stanzin Khenrab</h2>
    <span class="slogan">Open science, open minds.</span>

    <p>Paste the viewer URL below to get the direct download link for the PDF.</p>

    <input type="text" id="viewerUrl" placeholder="Paste Krishikosh viewer URL here..." />
    <button onclick="generateDownloadLink()">Get PDF</button>

    <div id="result" class="result" style="display:none;"></div>
  </div>

  <script>
    function generateDownloadLink() {
      const input = document.getElementById("viewerUrl").value.trim();
      const resultDiv = document.getElementById("result");
      resultDiv.style.display = "block";

      try {
        // Extract 'file' parameter from the URL
        const urlObj = new URL(input);
        const fileParam = urlObj.searchParams.get("file");

        if (!fileParam) {
          throw new Error("Invalid URL: Missing 'file' parameter.");
        }

        // Decode the URL
        const decodedUrl = decodeURIComponent(fileParam);

        resultDiv.className = "result success";
        resultDiv.innerHTML = `
          ✔️ Direct PDF Link:<br>
          <a href="${decodedUrl}" target="_blank" download>Click here to download</a>
        `;
      } catch (error) {
        resultDiv.className = "result error";
        resultDiv.innerHTML = `❌ Error: ${error.message}`;
      }
    }
  </script>

</body>
</html>
