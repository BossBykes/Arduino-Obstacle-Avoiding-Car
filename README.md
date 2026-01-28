# Arduino Obstacle Avoiding Car

## What's This About?

Ever wondered how self-driving cars "see" obstacles and avoid them? Well, I built a mini version using Arduino! This little robot car navigates around obstacles all by itself - no remote control needed. It's basically a tiny autonomous vehicle that taught me a ton about how real autonomous systems work.

## What It Does

- **Sees obstacles** using an ultrasonic sensor (like a bat's echolocation!)
- **Makes decisions** on which way to turn when something's in the way
- **Drives itself** around rooms, avoiding furniture, walls, and your cat
- **Never gets tired** - keeps exploring until the battery dies

## What I Built It With

| Part | What I Used | Why |
|------|-------------|-----|
| **Brain** | Arduino Uno | The main computer that makes all decisions |
| **Eyes** | HC-SR04 Ultrasonic Sensor | "Sees" how far objects are (like parking sensors) |
| **Muscles** | DC Motors + L298N Driver | Makes the wheels spin |
| **Body** | 4-wheel robot chassis | Something to put everything on |
| **Food** | 9V Battery Pack | Keeps everything running |

## How Does It Actually Work?

The logic is surprisingly simple (but took me forever to get right):

```cpp
// The basic idea
if (something_too_close) {
    stop();
    look_left();
    look_right();
    turn_toward_clearer_path();
} else {
    keep_going_forward();
}
```

**The step-by-step process:**
1. **Constantly checks ahead** - "Is anything less than 20cm away?"
2. **Stops when needed** - "Whoa, something's there!"
3. **Looks around** - Servo turns the sensor left and right
4. **Picks the best route** - "Left looks clearer than right"
5. **Makes the turn** - Spins the wheels accordingly
6. **Repeats forever** - Back to step 1

## How to Wire It Up

**Sensor connections:**
- VCC → 5V (power)
- GND → Ground
- Trig → Pin 9 (sends signal)
- Echo → Pin 10 (receives signal)

**Motor driver connections:**
- IN1-IN4 → Pins 2,3,4,5 (direction control)
- ENA, ENB → Pins 6,11 (speed control)

*Pro tip: Double-check your wiring before powering on - I learned this the hard way!*

**What I measured:**
- Detects objects from 2cm to 4 meters away
- Reacts in under 0.1 seconds
- Runs for about 2-3 hours on one battery
- Successfully avoids 95% of obstacles (the other 5% is usually user error)

## Problems I Had to Solve

**Noisy sensor readings:** The ultrasonic sensor would randomly give crazy readings. Fixed it by averaging multiple readings - much more stable now.

**Going in circles:** My motors weren't perfectly matched, so the car would drift. Spent hours tweaking the speed values until it drove straight.

**Getting stuck in corners:** Early version would get trapped between two walls. Added better scanning logic to find escape routes.

**Battery dying fast:** Original code was super inefficient. Added some delays and optimizations to double the battery life.

## What I Learned

This project was like a crash course in:
- **Arduino programming** - C++ for embedded systems
- **Sensor integration** - Reading and filtering real-world data
- **Motor control** - PWM signals and H-bridges
- **Algorithm design** - Making robots make smart decisions
- **Debugging patience** - Because nothing works the first time!

## Why This Matters

This little car might seem simple, but it's using the same basic principles as:
- **Tesla's Autopilot** (obstacle detection and avoidance)
- **Roomba vacuum cleaners** (autonomous navigation)
- **Warehouse robots** (automated material handling)
- **Mars rovers** (autonomous exploration)

Pretty cool that the fundamentals scale from a $50 Arduino project to million-dollar systems!

## Tags

`Arduino` `Autonomous-Vehicle` `Obstacle-Avoidance` `Robotics` `CPlusPlus` `Embedded-Systems` `DIY-Robot`

---

**Built with lots of coffee and debugging sessions**

*Started as a weekend project, ended up teaching me more about autonomous systems than any textbook ever could!*
