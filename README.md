

**1. Abstract**
<img width="4080" height="3072" alt="PXL_20260418_074142342" src="https://github.com/user-attachments/assets/2b98263a-245a-4b54-988f-1984cc15f4ac" />

This project is an experimental study of a tandem thrust-vectoring UAV
that is based on the shape of the CH-47 helicopter. The system uses two
inline propulsion units with servo-actuated tilt mechanisms to control
the attitude completely without using traditional aerodynamic surfaces.
The platform had very limited roll control, even though the actuators
were saturated, even though it was able to keep a stable pitch and yaw.
The study identifies geometric constraints, actuator nonlinearity, and
propulsion control coupling as the main factors that affect performance
through systematic testing, such as changing inertia and looking at how
actuators behave. The results show that there is a control authority
threshold below which actuator flaws control system behavior. This is
important information for my future VTOL and tilt-rotor designs.

**2. Objective**

The goal of this project is to see if a minimal tandem rotor UAV
configuration that only uses thrust vectoring for attitude control is
possible. The research seeks to examine axis-wise controllability,
discern constraints in roll dynamics, and evaluate the interplay between
actuator performance and control authority in underactuated systems.

**3. System Architecture**
<img width="4080" height="3072" alt="PXL_20260418_074153446" src="https://github.com/user-attachments/assets/783ff50b-88e6-44d9-8d32-dc1c64adf096" />

**3.1 Mechanical Layout**

The UAV has a tandem inline design, with two propulsion units placed
along the long axis. Each motor is attached to a servo-actuated tilt
mechanism that lets it move in two directions at once. The airframe has
a narrow lateral profile, which makes the structure less complicated but
limits the roll moment arm. A centrally mounted battery provides power,
which makes the setup compact but heavy with inertia.

**3.2 Control Strategy**
<img width="3072" height="4080" alt="PXL_20260418_074234153" src="https://github.com/user-attachments/assets/cbab39d8-c05e-4a1d-bd56-50af0a64310b" />

Attitude control is achieved through coordinated thrust vectoring:

Pitch: Both rotors tilt in the same direction.

Yaw: the difference in tilt between the front and back rotors\
Roll: Making lateral forces indirectly by using thrust components that
are caused by tilting\
\
The flight controller is based on a custom-configured INAV setup,
adapted through target-level modifications to support non-standard
actuator mapping and geometry.
<img width="3072" height="4080" alt="PXL_20260418_074158584" src="https://github.com/user-attachments/assets/b6339e48-a906-469d-8aa2-df0b97cf90e6" />

**4. Theoretical Framework**

**4.1 Torque Generation**

$$\tau = F \cdot r$$

The amount of torque that aerial systems can make depends on both the
force and the moment arm. While there was enough thrust, the inline
configuration made the lateral moment arm for roll very small, which
greatly limited torque generation.

**4.2 Rotational Dynamics**

$$\alpha = \frac{\tau}{I}$$

Angular acceleration depends on the ratio of applied torque to moment of
inertia. Experimental changes that increased inertia made the system
more stable and predictable but less responsive, confirming that the
system has limited torque.

**5. Experimental Investigations**

**5.1 Axis-wise Stability**

-   Pitch: Stable due to large longitudinal moment arm

-   Yaw: Responsive and controllable

-   Roll: Severely under-responsive despite maximum tilt angles (\~40°)

**5.2 Inertia Modification Experiment**

To make the roll moment of inertia higher, more carbon fiber tubes with
terminal masses of about 10 g each were added to the sides. The change
made the motion smoother and more predictable, but it didn\'t make roll
authority better. This demonstrates that higher inertia
dampens oscillations without fixing the problem of inadequate torque
being produced.
<img width="4080" height="3072" alt="PXL_20260418_074209735" src="https://github.com/user-attachments/assets/dfbe9e75-6e3f-48d4-bb03-aee5df6eeb71" />

**5.3 Actuator Behavior Analysis**

The servo-actuated tilt system struggled to center itself consistently,
which added random bias to the control loop. This caused constant
micro-correction and limit-cycle oscillations, which were especially
noticeable in the roll axis since it had low control authority.

**5.4 Thermal Observations**

The motors became extremely hot while hovering. This is due to constant
corrective inputs and inefficient use of thrust, which kept the system
in a constant state of control effort without reaching stable
equilibrium.

**6. Failure Analysis**

The system showcases a basic roll axis control authority restriction.
Just having the actuator range and thrust isn\'t good enough without the
lateral moment arm to generate torque. Furthermore, actuator
imperfections such as hysteresis and deadband inject process noise that
becomes dominant under low authority conditions. The two effects combine
to cause rolling behavior that cannot be predicted and roll oscillations
that do not decay naturally.
<img width="3072" height="4080" alt="PXL_20260418_074245946" src="https://github.com/user-attachments/assets/46303e76-91d0-45a6-8997-2e4cf5092ef0" />

**7. Key Findings**

-   Control effectiveness is determined by moment arm distribution, not
    thrust magnitude.

-   Actuator saturation does not give rise to a proportional response
    under the control-limited regime on which the system operates.

-   Adding inertia can improve the stabilization yet it decreases
    controllability.

-   When control authority is low, actuator imperfections will dictate
    the dynamics.

-   There is a minimum control authority threshold below which stable
    control cannot be consistently attained.

**8. Comparative Insight (Tricopter vs Bicopter)**

Previous implementation of a tricopter VTOL with the same servos
provided a stable performance despite lower roll authority due to
lateral motor separation. In contrast, the tandem bicopter\'s inline
geometry resulted in high sensitivity to actuator error. It shows,
therefore, how important is the geometric configuration on the system
robustness.

**9. Design Limitations**

-   Colinear thrust configuration keeps roll torque low

-   No aerodynamic control surfaces

-   High dependence on actuator precision

-   Propeller wake interaction affecting efficiency

**10. Conclusion**

This project demonstrates that thrust-vectoring alone is insufficient
for stable control in geometrically constrained configurations. The
study highlights the interplay between mechanical design, actuator
behavior, and control strategy, emphasizing the need for integrated
system-level optimization in UAV development.


Test https://youtu.be/YouTH7BKoaU

