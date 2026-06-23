## 0. Experiment with rocket trajectories in Hohmann transfers

## 1. Hohmann Transfer Mechanics

A **Hohmann transfer** moves a satellite from one circular orbit to another, larger or smaller, circular orbit using exactly two engine burns. An example of this may be a trans-lunar injection (TLI) from low earth orbit (LEO) to a lunar orbit, though it may be used to get into any other orbit, as in a Medium Earth Orbit (MEO) or a Geostationary Orbit (GEO). Burn 1 kicks the satellite out of its initial circular orbit into an elliptical *transfer orbit*, usually when the spacecraft is at its perigee (the closest point to Earth in its orbit) in a “**Oberth effect**”. The satellite coasts along this ellipse, engines off and letting gravity do the work so to speak, until it reaches the new desired radius, at which point Burn 2 kicks it back into a circular orbit at that radius.

As a quick homage, the principle arises from the thought experiment of **”Newton's cannon”**: a projectile fired too slowly falls back to Earth; fired too fast, it flies off into space; fired at exactly the right speed for its altitude, it stays in circular orbit. Speeding a satellite up in circular orbit breaks the balance between gravity and velocity (potential and kinetic energy), and it drifts outward along an elliptical path in concordance with Kepler’s laws of orbital motion; whereas an object moves fastest when it’s nearest the body it orbits, increasing tangential velocity at perigee kicks up the size of the major axis of the elliptical path (we will see what happens if *radial* velocity instead increases). Slowing back down at the new radius restores the energy balance, locking it into a new circular orbit.

The two questions a Hohmann transfer answers are: how much speed must be added at each burn (the $\Delta V$ budget), and how long does the coast between burns take.

#### 1a. Velocity in Circular Orbit

For a satellite in circular orbit, gravity supplies the centripetal force, as in:

$$
\frac{mv^2}{r} = \frac{GM_E m}{r^2}
$$

Mass $m$ and one factor of $r$ cancel, leaving:

$$
v^2 = \frac{GM_E}{r}
$$

It's standard to define $\mu = GM_E$, the gravitational parameter of the central body, so this becomes:

$$
\boxed{v = \sqrt{\frac{\mu}{r}}}
$$

This is the speed required to hold a circular orbit at radius $r$. Applied to the initial orbit (radius $r_1$) and final orbit (radius $r_2$):

$$
V_1 = \sqrt{\frac{\mu}{r_1}}, \qquad V_{final} = \sqrt{\frac{\mu}{r_2}}
$$

Note that smaller $r$ means _larger_ $v$, as we stated in the last section. Low orbits move fast; high orbits move slow, as in *Kepler’s Third Law*.

#### 1b. Energy Equations

To figure out how the satellite's speed changes as it moves along the elliptical transfer path, we need a quantity that stays constant along that path. As long as the only force acting is gravity, that quantity is the **mechanical energy**.

$$
E = \frac{1}{2}mv^2 + U, \qquad U = -\frac{GM_E m}{r}
$$

Gravitational potential energy is negative by convention and derived from the force relation, $F=-\nabla U$. So mechanical energy is:

$$
E = \frac{1}{2}mv^2 - \frac{GM_E m}{r}
$$

For a circular orbit, substitute $v^2 = \mu/r$ from Section 1:

$$
E = \frac{1}{2}m\frac{\mu}{r} - \frac{\mu m}{r} = -\frac{\mu m}{2r}
$$

$$
\boxed{E_{\text{circular}} = -\frac{\mu m}{2r}}
$$

So now we have an expression for the energy of the circular orbit in terms of $\mu$ in addition to the velocity $v$. The same expression holds for an elliptical orbit, with $r$ replaced by the ellipse's semi-major axis $a$:

$$
\boxed{E_{\text{elliptical}} = -\frac{\mu m}{2a}}
$$

Since mechanical energy is conserved along the transfer ellipse, computing $E_{\text{elliptical}}$ once tells you the satellite's energy — and therefore speed, via the equation above — at *every* point along that ellipse, including both burn points!

The transfer ellipse is tangent to the initial circular orbit at one end and the final circular orbit at the other. Imagine the initial, lower circular orbit and the ellipse that spawns after Burn 1; the circular orbit sits within the ellipse. Then at the point of Burn 2, both figures would lie within the broader circular orbit. Therefore, the ellipse's full major axis spans from $r_1$ on one side of the central body to $r_2$ on the other. If $a$ is the semi-major axis:

$$
2a = r_1 + r_2
$$

$$
\boxed{a = \frac{r_1 + r_2}{2}}
$$

The near point of this ellipse (radius $r_1$) is called *periapsis*. The far point (radius $r_2$) is *apoapsis*. Burn 1 happens at periapsis; Burn 2 happens at apoapsis.

At Burn 1 point, the satellite is still at radius $r_1$, but its mechanical energy has just changed to that of the transfer ellipse. Setting the elliptical energy equal to kinetic plus potential energy at $r_1$:

$$
-\frac{\mu m}{2a} = \frac{1}{2}mV_2^2 - \frac{\mu m}{r_1}
$$

Dividing through by $m$ and solving for $V_2$, the speed immediately after Burn 1 should be:

$$
\boxed{V_2 = \sqrt{\mu\left(\frac{2}{r_1} - \frac{1}{a}\right)}}
$$

The same equation applies at $r_2$, giving $V_3$, the speed immediately *before* Burn 2:

$$
\boxed{V_3 = \sqrt{\mu\left(\frac{2}{r_2} - \frac{1}{a}\right)}}
$$

$V_2$ is faster than $V_1$ since the satellite has sped up to leave its circular orbit. But by the time it reaches $r_2$, $V_3$ is *slower* than $V_4$, the speed needed to hold a stable circular orbit there, again in concordance with Kepler’s Third. It arrives at apoapsis moving too slowly to stay in circular orbit — which is precisely why Burn 2 is needed.

## 2. Delta-V Budget

Burn 1 takes the satellite from its circular orbit speed $V_1$ up to the transfer ellipse speed $V_2$:

$$
\boxed{\Delta V_1 = V_2 - V_1}
$$

Burn 2 takes it from the transfer ellipse speed $V_3$ up to the new circular orbit speed $V_4$:

$$
\boxed{\Delta V_2 = V_4 - V_3}
$$

The total propulsive cost of the maneuver is the sum of the magnitudes of both burns:

$$
\boxed{\Delta V_{\text{total}} = |\Delta V_1| + |\Delta V_2|}
$$

This is the number that matters operationally — it's what feeds into the rocket equation to determine how much propellant the maneuver actually costs.

#### 2a. Transfer Time

The transfer ellipse is a real but temporary orbit and obeys Kepler's Third Law, which relates orbital period to semi-major axis:

$$
T^2 = \frac{4\pi^2}{\mu}a^3
$$

But the satellite doesn't travel the full ellipse — it only travels from periapsis to apoapsis, exactly half the orbit. So the time between Burn 1 and Burn 2 is half the full period:

$$
t_{\text{transfer}} = \frac{T}{2} = \frac{1}{2}\sqrt{\frac{4\pi^2}{\mu}a^3}
$$

Substituting $a = (r_1+r_2)/2$ from Section 1:

$$
\boxed{t_{\text{transfer}} = \frac{\pi}{\sqrt{\mu}}\left(\frac{r_1+r_2}{2}\right)^{3/2}}
$$
