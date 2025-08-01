<!DOCTYPE html>
<html>
<head>
  <title>📍 GPS Attendance</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {font-family: Arial; padding: 20px; background: #f5f5f5;}
    .form {background: #fff; padding: 20px; border-radius: 12px; max-width: 400px; margin: auto; box-shadow: 0 0 10px #ccc;}
    input, select, textarea, button {width: 100%; padding: 10px; margin: 10px 0; border-radius: 6px; border: 1px solid #ccc;}
    button {background: #10b981; color: white; font-weight: bold;}
  </style>
</head>
<body>
  <div class="form">
    <h2>📍 GPS Attendance</h2>
    <form id="form">
      <input type="text" name="name" placeholder="👤 Name" required />
      <select name="shift" required>
        <option value="">🕒 Shift</option>
        <option value="Morning">Morning</option>
        <option value="Evening">Evening</option>
        <option value="Night">Night</option>
      </select>
      <input type="text" name="location" id="location" placeholder="🌍 Location" readonly required />
      <textarea name="remarks" placeholder="📝 Remarks"></textarea>
      <button type="submit">✅ Submit</button>
    </form>
  </div>

  <script>
    navigator.geolocation.getCurrentPosition(position => {
      document.getElementById("location").value = position.coords.latitude + ", " + position.coords.longitude;
    }, () => {
      alert("⚠️ Please allow location access and refresh.");
    });

    const form = document.getElementById("form");
    form.addEventListener("submit", e => {
      e.preventDefault();
      fetch('YOUR_WEB_APP_URL_HERE', {
        method: 'POST',
        body: new FormData(form)
      }).then(() => {
        alert("✅ Attendance submitted!");
        form.reset();
      }).catch(() => {
        alert("❌ Submission failed.");
      });
    });
  </script>
</body>
</html>
