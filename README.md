<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🔥 Job Board</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f7f9fc;
      margin: 0;
      padding: 0;
    }

    .container {
      width: 90%;
      max-width: 800px;
      margin: 30px auto;
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    }

    h1, h2 {
      color: #333;
    }

    form {
      margin-top: 20px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    input, textarea {
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      font-size: 1rem;
    }

    button {
      background-color: #007bff;
      color: white;
      border: none;
      padding: 12px;
      border-radius: 5px;
      font-size: 1rem;
      cursor: pointer;
    }

    button:hover {
      background-color: #0056b3;
    }

    .job-card {
      border: 1px solid #ddd;
      padding: 15px;
      border-radius: 8px;
      margin-bottom: 15px;
      background-color: #fafafa;
    }

    .job-card h3 {
      margin: 0;
      color: #007bff;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>🔥 Job Board</h1>
    <h2>Post a Job</h2>
    <form id="job-form">
      <input type="text" id="title" placeholder="Job Title" required>
      <input type="text" id="company" placeholder="Company Name" required>
      <textarea id="description" placeholder="Job Description" required></textarea>
      <button type="submit">Post Job</button>
    </form>
    <div id="job-list"></div>
  </div>

  <script>
    const jobForm = document.getElementById('job-form');
    const jobList = document.getElementById('job-list');
    let jobs = [];

    jobForm.addEventListener('submit', (e) => {
      e.preventDefault();

      const title = document.getElementById('title').value.trim();
      const company = document.getElementById('company').value.trim();
      const description = document.getElementById('description').value.trim();

      if (title && company && description) {
        const job = { title, company, description };
        jobs.push(job);
        renderJobs();
        jobForm.reset();
      }
    });

    function renderJobs() {
      jobList.innerHTML = '';
      jobs.forEach((job, index) => {
        const jobCard = document.createElement('div');
        jobCard.className = 'job-card';
        jobCard.innerHTML = `
          <h3>${job.title}</h3>
          <p><strong>Company:</strong> ${job.company}</p>
          <p>${job.description}</p>
          <button onclick="deleteJob(${index})">Delete</button>
        `;
        jobList.appendChild(jobCard);
      });
    }

    function deleteJob(index) {
      jobs.splice(index, 1);
      renderJobs();
    }
  </script>
</body>
</html>
