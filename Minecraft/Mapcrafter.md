# Mapcrafter

> https://github.com/mapcrafter/mapcrafter

```sh
/usr/local/bin/mapcrafter_markers -c /path/to/render.conf >> /path/to/mapcrafter.log 2>&1 && \
/usr/local/bin/mapcrafter -j 4 -c /path/to/render.conf >> /path/to/mapcrafter.log 2>&1
```

### render.conf

```vim
output_dir = /path/to/output
background_color = #ffffff

[global:map]
world = survival
render_mode = daylight
texture_size = 12
image_format = png
png_indexed = true

[world:survival]
input_dir = /path/to/world
crop_center_x = 0
crop_center_z = 0
crop_radius = 10000
default_zoom = 3

[map:survivalday]
name = 3D
render_view = isometric
rotations = top-left

[map:survivalday2d]
name = 2D
render_view = topdown
```
