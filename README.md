
  function createHeartExplosion(x, y) {
    const colors = ["#ff66cc", "#ff99cc", "#ffb6c1", "#ffc0cb", "#ffe6f2"];
    const count = 50;
    const scale = 8;

    for (let i = 0; i < count; i++) {
      const t = Math.PI * 2 * (i / count);
      const xOffset = 16 * Math.pow(Math.sin(t), 3);
      const yOffset = 13 * Math.cos(t) - 5 * Math.cos(2 * t) - 2 * Math.cos(3 * t) - Math.cos(4 * t);

      const heart = document.createElement("div");
      heart.className = "heart";
      heart.textContent = "💖";
      heart.style.color = colors[i % colors.length];
      heart.style.left = `${x}px`;
      heart.style.top = `${y}px`;

      heart.style.setProperty('--x', `${xOffset * scale}px`);
      heart.style.setProperty('--y', `${-yOffset * scale}px`);

      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 1800);
    }
  }

  document.addEventListener("click", (e) => {
    createHeartExplosion(e.clientX, e.clientY);
  });

  document.addEventListener("touchstart", (e) => {
    const touch = e.touches[0];
    createHeartExplosion(touch.clientX, touch.clientY);
  });
</script>

</body>
</html>
