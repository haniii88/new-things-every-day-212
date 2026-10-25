```javascript
function dailyLog212() {
  const connections = [
    { name: "Wi-Fi", latency: 24, packetLoss: 0 },
    { name: "Mobile Data", latency: 85, packetLoss: 2 },
    { name: "VPN", latency: 140, packetLoss: 5 },
    { name: "Ethernet", latency: 12, packetLoss: 0 },
    { name: "Public Wi-Fi", latency: 210, packetLoss: 8 },
  ];

  const averageLatency =
    connections.reduce((sum, item) => sum + item.latency, 0) /
    connections.length;

  const unreliable = connections.filter(
    item => item.latency > 150 || item.packetLoss > 3
  );

  const fastest = connections.reduce((best, item) =>
    item.latency < best.latency ? item : best
  );

  console.log("=== Network Performance Report ===");
  console.log(`Connections Tested: ${connections.length}`);
  console.log(`Average Latency: ${averageLatency.toFixed(1)} ms`);
  console.log(`Fastest Connection: ${fastest.name}`);
  console.log(`Unreliable Connections: ${unreliable.length}`);

  console.log("\n=== Connection Details ===");

  connections.forEach(item => {
    const status =
      item.latency > 150 || item.packetLoss > 3
        ? "⚠️ Needs Attention"
        : "✅ Stable";

    console.log(
      `${item.name}: ${item.latency} ms, ` +
      `Packet Loss: ${item.packetLoss}% — ${status}`
    );
  });
}

dailyLog212();
```
