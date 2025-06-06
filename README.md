<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Instant Fence Estimate</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; }
    iframe { width: 100%; height: 400px; border: 1px solid #ccc; }
    .form-section { margin-top: 20px; }
    input, select, button { display: block; margin: 10px 0; padding: 8px; width: 100%; max-width: 400px; }
  </style>
</head>
<body>
  <h1>Get an Instant Fence Estimate</h1>
  <p>Use the map below to trace your fence line and estimate the length in feet. Enter the measurement and options below for a fast quote.</p>

  <!-- Embed a free map measuring tool -->
  <iframe src="https://www.mapdevelopers.com/draw-circle-tool.php"></iframe>

  <div class="form-section">
    <form id="estimateForm">
      <label for="length">Fence Length (in feet)</label>
      <input type="number" id="length" name="length" required />

      <label for="fenceType">Fence Type</label>
      <select id="fenceType" name="fenceType">
        <option value="28">Wood Privacy ($28/ft)</option>
        <option value="22">Chain Link ($22/ft)</option>
        <option value="35">Vinyl ($35/ft)</option>
      </select>

      <label for="gates">Number of Gates</label>
      <input type="number" id="gates" name="gates" value="0" />

      <button type="submit">Calculate Estimate</button>
    </form>

    <h3 id="result"></h3>
  </div>

  <script>
    const form = document.getElementById("estimateForm");
    const result = document.getElementById("result");

    form.addEventListener("submit", function (e) {
      e.preventDefault();

      const length = parseFloat(document.getElementById("length").value);
      const rate = parseFloat(document.getElementById("fenceType").value);
      const gates = parseInt(document.getElementById("gates").value);

      const fenceCost = length * rate;
      const gateCost = gates * 250; // Flat $250 per gate
      const total = fenceCost + gateCost;

      result.textContent = `Estimated Price: $${total.toLocaleString()}`;
    });
  </script>
</body>
</html>

