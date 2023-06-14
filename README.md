<!DOCTYPE html>
<html>
<head>
    <title>Auto Drip Control</title>
    <style>
        body {
            font-family: "Segoe UI", Arial, sans-serif;
            background-color: #f7f7f7;
        }
        
        h1 {
            color: #333;
            text-align: center;
            margin-top: 30px;
        }
        
        .sensor {
            margin-bottom: 20px;
            background-color: #fff;
            padding: 10px;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .sensor label {
            font-weight: bold;
            color: #333;
        }
        
        .valve-status {
            margin-top: 20px;
            font-weight: bold;
            color: #333;
        }
        
        .valve-control {
            margin-top: 20px;
            display: flex;
            justify-content: center;
        }
        
        .valve-control button {
            margin: 0 10px;
            padding: 10px 20px;
            font-weight: bold;
            background-color: #4CAF50;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        
        .valve-control button:hover {
            background-color: #45a049;
        }
        
        .picture {
            text-align: center;
            margin-top: 30px;
        }
        
        .picture img {
            max-width: 300px;
            height: auto;
        }
    </style>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script>
        $(document).ready(function() {
            // Function to update sensor readings and valve status
            function updateData() {
                // Send AJAX request to server to get sensor readings and valve status
                $.ajax({
                    url: "/data",
                    type: "GET",
                    dataType: "json",
                    success: function(data) {
                        // Update sensor readings
                        $("#moisture1").text(data.moisture1);
                        $("#moisture2").text(data.moisture2);
                        $("#moisture3").text(data.moisture3);
                        $("#temperature1").text(data.temperature1);
                        $("#temperature2").text(data.temperature2);
                        $("#temperature3").text(data.temperature3);
                        
                        // Update valve status
                        $("#valve-status1").text("Valve 1 Status: " + data.valveStatus1);
                        $("#valve-status2").text("Valve 2 Status: " + data.valveStatus2);
                        $("#valve-status3").text("Valve 3 Status: " + data.valveStatus3);
                    },
                    error: function(xhr, status, error) {
                        console.log("Error:", error);
                    }
                });
            }
            
            // Start updating data every 2 seconds
            setInterval(updateData, 2000);
            
            // Function to control valve 1
            $("#control-button1").click(function() {
                // Send AJAX request to server to control valve 1
                $.ajax({
                    url: "/control",
                    type: "POST",
                    data: { valve: 1 },
                    success: function(response) {
                        alert(response.message);
                    },
                    error: function(xhr, status, error) {
                        console.log("Error:", error);
                    }
                });
            });
            
            // Function to control valve 2
            $("#control-button2").click(function() {
                // Send AJAX request to server to control valve 2
                $.ajax({
                    url: "/control",
                    type: "POST",
                    data: { valve: 2 },
                    success: function(response) {
                        alert(response.message);
                    },
                    error: function(xhr, status, error) {
                        console.log("Error:", error);
                    }
                });
            });
            
            // Function to control valve 3
            $("#control-button3").click(function() {
                // Send AJAX request to server to control valve 3
                $.ajax({
                    url: "/control",
                    type: "POST",
                    data: { valve: 3 },
                    success: function(response) {
                        alert(response.message);
                    },
                    error: function(xhr, status, error) {
                        console.log("Error:", error);
                    }
                });
            });
        });
    </script>
</head>
<body>
    <h1>Automated Drip Irrigation Control</h1>

      <p>Project members:
        1. Chinmoy Kalita
        2. Risha Subbaiah
        3. Rakshita P V 
        4. Vignesha</p>
     
      <p>Under the guidance of :
        Dr. Viresh Kumargoud
      </p>
    
    <div class="sensor">
        <label>Sensor 1 Moisture:</label> <span id="moisture1">-</span>
    </div>
    <div class="sensor">
        <label>Sensor 2 Moisture:</label> <span id="moisture2">-</span>
    </div>
    <div class="sensor">
        <label>Sensor 3 Moisture:</label> <span id="moisture3">-</span>
    </div>
    
    <div class="sensor">
        <label>Sensor 1 Temperature:</label> <span id="temperature1">-</span>
    </div>
    <div class="sensor">
        <label>Sensor 2 Temperature:</label> <span id="temperature2">-</span>
    </div>
    <div class="sensor">
        <label>Sensor 3 Temperature:</label> <span id="temperature3">-</span>
    </div>
    
    <div class="valve-status" id="valve-status1">Valve 1 Status:</div>
    <div class="valve-status" id="valve-status2">Valve 2 Status:</div>
    <div class="valve-status" id="valve-status3">Valve 3 Status:</div>
    
    <div class="valve-control">
        <button id="control-button1">Control Valve 1</button>
        <button id="control-button2">Control Valve 2</button>
        <button id="control-button3">Control Valve 3</button>
    </div>
    
    <div class="picture">
        <img src="https://st3.depositphotos.com/2631141/15987/i/450/depositphotos_159870806-stock-photo-young-tomato-plants-drip-irrigation.jpg" alt="Drip Irrigation 1">
    </div>
    
    <div class="picture">
        <img src="https://st.depositphotos.com/1577237/3279/i/450/depositphotos_32793155-stock-photo-irrigation.jpg" alt="Drip Irrigation 2">
    </div>
</body>
</html>
