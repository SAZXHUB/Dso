<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Network Packet Sender</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 p-8">
    <div class="max-w-md mx-auto bg-white p-6 rounded-lg shadow-lg">
        <h1 class="text-2xl font-bold mb-4 text-center">Network Packet Sender</h1>
        <form id="packetForm" class="space-y-4">
            <div>
                <label class="block mb-2">Website URL</label>
                <input type="text" id="urlInput" required 
                    class="w-full px-3 py-2 border rounded-md" 
                    placeholder="example.com">
            </div>
            <div>
                <label class="block mb-2">Port Number</label>
                <input type="number" id="portInput" required 
                    class="w-full px-3 py-2 border rounded-md" 
                    placeholder="80">
            </div>
            <div>
                <label class="block mb-2">Protocol</label>
                <select id="protocolInput" 
                    class="w-full px-3 py-2 border rounded-md">
                    <option value="tcp">TCP</option>
                    <option value="udp">UDP</option>
                </select>
            </div>
            <div>
                <label class="block mb-2">Packet Size (bytes)</label>
                <input type="number" id="packetSizeInput" 
                    class="w-full px-3 py-2 border rounded-md" 
                    value="1024">
            </div>
            <div>
                <label class="block mb-2">Packet Count</label>
                <input type="number" id="packetCountInput" 
                    class="w-full px-3 py-2 border rounded-md" 
                    value="1024">
            </div>
            <button type="submit" 
                class="w-full bg-blue-500 text-white py-2 rounded-md hover:bg-blue-600">
                Send Packets
            </button>
        </form>
        <div id="outputArea" class="mt-4 p-3 bg-gray-50 rounded-md h-40 overflow-y-auto"></div>
    </div>

    <script>
        document.getElementById('packetForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const url = document.getElementById('urlInput').value;
            const port = document.getElementById('portInput').value;
            const protocol = document.getElementById('protocolInput').value;
            const packetSize = document.getElementById('packetSizeInput').value;
            const packetCount = document.getElementById('packetCountInput').value;
            const outputArea = document.getElementById('outputArea');

            outputArea.innerHTML = ''; // Clear previous output

            for (let i = 0; i < packetCount; i++) {
                const packetInfo = document.createElement('div');
                packetInfo.textContent = `${protocol.toUpperCase()} Packet ${i+1} sent to ${url}:${port}`;
                outputArea.appendChild(packetInfo);
            }

            alert(`Sent ${packetCount} ${protocol.toUpperCase()} packets to ${url}:${port}`);
        });
    </script>
</body>
</html>
