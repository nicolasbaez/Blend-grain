# Blend-grain
I'm radiating horrible energy today.

![buh](https://github.com/nicolasbaez/Blend-grain/blob/main/xp063.gif)
```javascript
setup = (_) => createCanvas((w = 500), w);
n = 3;
k = 0;
draw = (_) => {
  background(0);
  noFill();
  for (j = 0; j < w; j += w / 128) {
    beginShape();
    for (i = 0; i <= w; i += w / 32) {
      c = (noise(j * 0.01, k * 0.01, i * 0.01) * w) / 2;
      h = map(i, 0, w, 0, c);
      stroke(c);
      vertex(i, map(sin(map(i + k, 0, w, 0, n * PI)), -1, 1, j - h, j + h));
    }
    endShape();
  }
  if (k == 0) saveGif("xp063.gif", 200, { delay: 0, units: "frames" });
  k -= 0.9;
};
