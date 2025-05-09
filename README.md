<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Accessible Photo Gallery</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
    }
    #gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
    }
    figure {
      border: 2px solid #ccc;
      padding: 10px;
      border-radius: 10px;
    }
    img {
      max-width: 100%;
      height: auto;
      display: block;
    }
    figcaption {
      margin-top: 5px;
      text-align: center;
    }
    figure:focus {
      outline: 3px solid #007ACC;
      background-color: #f0f8ff;
    }
  </style>
</head>
<body onload="addTabIndex()">
  <h1>Accessible Photo Gallery</h1>
  <section id="gallery">
    <figure>
      <img src="photo1.jpg" alt="Sunset over mountains">
      <figcaption>Sunset View</figcaption>
    </figure>
    <figure>
      <img src="photo2.jpg" alt="A forest with sunlight streaming through the trees">
      <figcaption>Morning Forest</figcaption>
    </figure>
    <figure>
      <img src="photo3.jpg" alt="City skyline at night with lights reflected on water">
      <figcaption>City Nights</figcaption>
    </figure>
  </section>

  <script>
    function addTabIndex() {
      const figures = document.querySelectorAll('figure');
      figures.forEach((fig, index) => {
        fig.setAttribute('tabindex', index + 1);
        fig.addEventListener('mouseover', () => {
          fig.style.borderColor = '#007ACC';
        });
        fig.addEventListener('mouseout', () => {
          fig.style.borderColor = '#ccc';
        });
        fig.addEventListener('keydown', (e) => {
          if (e.key === "Enter") {
            alert(`You selected: ${fig.querySelector('figcaption').innerText}`);
          }
        });
      });
    }
  </script>
</body>
</html>
