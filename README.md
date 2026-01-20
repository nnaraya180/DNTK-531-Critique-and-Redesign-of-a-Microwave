# DNTK-531-Critique-and-Redesign-of-a-Microwave
DNTK 531 Week 1 assignment: Critique and Redesign of an Everyday Object


___
##1. Object Analysis & Missing Affordances
**Use Scenario**
It’s late, and the kitchen is quiet except for the low hum of the microwave as it accepts my best guess for the time to heat my food 1:30, not because it’s right, but because it’s familiar. Behind the glass, a bowl of leftovers turns slowly, steam fogging and clearing in uneven pulses, while the display offers the only thing it knows how to show: time counting down. The machine has no idea what’s inside—rice, soup, something fragile or something dense—and no sense of how heat is actually moving through it. It can’t hear the soft sizzle or the warning pop of pressure building. It doesn’t know it’s night, or that a loud beep will cut through a sleeping apartment. So I stay nearby, watching, listening, ready to intervene. When it stops, I stir and find the same truth I always do: edges too hot, center still cold. I add thirty more seconds and hover again, acting as the microwave’s eyes, ears, and judgment, finishing the work it never knew it was missing.

**The Gap**
- The microwave does not know what it is heating: Food, material, mass, and moisture are invisible to it. A paper plate is treated the same as ceramic; aluminum is indistinguishable until it sparks.
- It has no awareness of the food’s actual state: Starting state, Internal temperature, heat distribution, and thermal inertia are unknown.
- It cannot sense the environment it creates: Steam accumulates unnoticed. Humidity builds until food turns soggy and the interior drips with condensation
- The microwave is deaf to the sounds of cooking: auditory cues humans rely on to prevent failure
- It does not know who is using it: 
- Its feedback is incomplete: Time remaining is the only visible signal, even though time is the least meaningful variable. The microwave does not show temperature, heating progress, or unevenness, nor does it explain what it is doing or why.
- It does not adapt to context or habit: The microwave behaves the same at noon and at midnight. It does not learn that a user always adds thirty more seconds, or that loud alerts disrupt shared living spaces.
- It waits for explicit instruction instead of anticipating intent: Defrosting ends, and the user must decide what comes next. Dense foods overcook because the machine waits for a target instead of predicting what will happen after it stops.
- The microwave externalizes its intelligence onto the user: The user watches, listens, stirs, guesses, restarts, and hovers—acting as the device’s missing sensors and judgment.

**Opportunity**
The microwave could move from a time-based appliance to a state-aware one. Using computer vision and embedded sensors, it could recognize what is placed inside like a food, container, mass, and moisture and track internal temperature, heat distribution, and humidity as cooking unfolds. Instead of guessing with fixed power and time, the microwave would adjust dynamically, responding to steam, sound, and thermal inertia to prevent sogginess, spills, or overcooking. It could adapt to context and habit, softening alerts at night, learning preferred doneness, and transitioning seamlessly between defrosting and cooking without manual intervention. In doing so, the microwave would no longer rely on the user to monitor, interrupt, and correct the process, but would assume responsibility for the outcome it initiates.

**Justification**
Filling these gaps is worth the added complexity because the microwave already imposes hidden costs on users through constant monitoring, repeated corrections, wasted food, and social friction. What appears to be a simple appliance routinely demands attention, judgment, and interruption—especially in shared or late-night contexts—turning reheating into a supervised task rather than a background one. By internalizing sensing and decision-making, the microwave reduces cognitive load, prevents common failures before they occur, and increases trust in everyday use. The added intelligence does not replace user control but removes the need for vigilance.

___
##2. Propose a Redesign

**Design Rationale**
The redesign prioritizes awareness of what is being heated along with real-time sensing of internal temperature, heat distribution, and humidity. By surfacing this information through clearer feedback and adapting power, time, and signaling dynamically, the microwave shifts from a static, time-based device to one that responds to the physical reality of cooking as it unfolds. This redesign focuses on more accurate heating alleviating the user of a guessing game and monitoring the food. The proposed features also prioritize a better UI by using signaling and communication with the user.
Gaps related to auditory cooking cues and user identity recognition were intentionally excluded to limit system complexity and redundancy in features, focusing instead on sensing modalities that offer impact for improving core reheating behavior and the users cognitive load.

**Proposed Features**
- Internal computer vision camera: Identifies what’s inside (food category + container type), estimates portion size, and detects risky conditions (metallic surfaces, sealed lids, overflowing liquids). Vision classification/generalization is the core problem—ML is better at messy variation.
- IR thermal sensor: Multi-point temperature Estimates surface temperature and heating uniformity, enables heat-until-ready instead of heat-for-time.
- Humidity / steam sensor: Detects moisture buildup that leads to sogginess and condensation; supports humidity-aware heating profiles.
- Weight sensor: Measures portion mass, detects boil-over/spill events (rapid weight shift), and improves time-to-temp estimates by grounding the model in actual load.
- Active vent / dehumidifying fan cycle: manage humidity and reduce sogginess + interior condensation.
- Heat map displayed on door: Shows the heating progress of food instead of solely relying on time remaining.
- A threshold-based microwave can only react to single sensor triggers (e.g., humidity above X, temp above Y), but heating quality depends on context: food type, container, portion size, starting temperature, and how those variables change over time. The same humidity spike can mean “perfect steaming” for one dish and “soggy failure” for another; the same surface temperature can hide a cold center in dense foods. ML is needed to fuse multiple signals and predict outcomes so the system can make reliable, food-specific adjustments rather than brittle one-size-fits-all rules.

**Social Considerations**
The redesigned microwave largely preserves existing habits rather than introducing new ones. Users still place food inside and start a cycle, but the amount of input is reduced. Most intelligence operates in the background, making the system feel normalized and largely invisible.The heat map and status messages function as quiet reassurance, not spectacle, and can be ignored by users who prefer minimal interaction. Social cost is reduced rather than introduced: adaptive signaling prevents loud alerts during late-night use, and proactive prompts around spills or uneven heating shift accountability from roommates to the device itself, easing shared-space tension. Because the interaction model remains familiar and uses daily normal conventions, the microwave does not require justification or technical explanation to be used comfortably by others. In everyday contexts, it behaves less like a “smart device” and more like a dependable appliance that simply works better.

**Tradeoff Analysis**
This redesign introduces additional complexity through the integration of multiple sensors, cameras, and control systems, each of which represents a potential point of failure. Components must be carefully shielded from heat, steam, grease, and food residue, and designed to withstand repeated thermal cycling while remaining easy to clean and sanitize. Increased sensing and computation also raise manufacturing cost, power consumption, and repair complexity compared to traditional microwaves. Software-driven behavior introduces new failure modes, including sensor drift, misclassification, or degraded performance over time if models are not robust or well-calibrated. 
