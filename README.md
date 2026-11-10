# Flower-
import turtle as t, math as m

s = t.Screen(); s.setup(600, 700); s.bgcolor("#020204"); s.tracer(0)
p = t.Turtle(); p.hideturtle()

def draw_layer(max_r, offset_deg, steps, is_red=False):
    offset = m.radians(offset_deg)
    for i in range(steps, 0, -1):
        f = i / steps
        if is_red:
            col = f"#{int(255*(f**0.5)):02x}{int(20*f):02x}{int(30*f):02x}"
        else:
            v = int(255 * (f ** 0.55))
            col = f"#{v:02x}{v:02x}{v:02x}"
            
        p.color(col)
        for k in range(8):
            petal_angle = offset + k * (m.pi / 4)
            p.penup()
            first = True
            for j in range(-15, 16):
                phi = (j / 15) * (m.pi / 8)
                r = max_r * f * (m.cos(4 * phi) ** 0.45)
                ang = petal_angle + phi
                x = r * m.cos(ang)
                y = r * m.sin(ang)
