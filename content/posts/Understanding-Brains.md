---
title: "Understanding Brains"
date: 2021-10-11T09:53:04+05:30
draft: true
---

__This article has been in the works since July 2020. Putting this up to remind myself occasionally.__

- ## What's needed before we can firmly say - "Yes, now we understand how brains work"?
    - When we can simulate some person's brain? When we can scan any person's brain and simulate it perfectly?
    - When we can extract out the useful bits from brain development and encode it in a more efficient form in silicon?
    - When we can create new brains with tweakable parameters, while correcting for every mistake, malformed circuits, chemical imbalances, developmental issues (chronic depression, schizo, bipolar, ocd)? [[Brain Simulation]]
    - What would it take? And how could we get there?
- 
- ### Physics can model everything, but we can't use it to model most things
    - Whatever is the lowest level moving parts of the universe - Quantum Mechanics, String Theory, etc. can in theory be used to explain and predict everything we see. But we simply don't have the means to do that. We'll essentially have to simulate a universe.
    - That's why our models are essentially flawed. The goal is to **move towards less flawed, less biased models from more flawed ones**.
- 
- ## What do we already know?
    - Force assumptions out in the open. What do we know?
        - different brain regions that do different tasks
            - Visual cortex for vision, pre-frontal cortex for non-automatic decision making, cerebellum for movement ...
        - there are excitatory and inhibitory neurons
        - there are many kinds of **neurotransmitters**, each having subtly/glaringly different functions
            - Most well known ones being Glutamine, Dopamine, Serotonin, GABA, acetylcholine. But there are TONS of less well known ones. Their functions range from well(excitatory/inhibitory) to poorly understood
        - individual Neurons differ wildly in functional properties
            - different neurons have different transmission speeds. Depends on many things, including myelination, thickness of fibre, etc.
                - speeds can change with time
            - Otther params like firing threshold, rebound spikes, stuttering, changing interspike interval, etc.
        - brains are **plastic**. Hebbian rule is an approximate local learning rule. Perhaps some short-range backprop also.
            - Predictive processing as approximation for learning rule
    - __How to convert these to falsifiable hypotheses? Are we >95% sure about any of these?__
- 
- # Angles of attack
- ## Brain development
    - Cell -> foetus -> baby -> teen -> adult.
    - Are there local rules that tell cells where to divide, where to connect, where to form which cells? Are there 'practice signals' to shape the neural pathways crudely?
    - See [Orphanogenesis](https://www.gregegan.net/DIASPORA/01/Orphanogenesis.html) - shapers, screamers, local rules, start out with highly generic computational medium.
    - Which brain regions form first out of the "nerve tube" of the fetus?
    - How does the brain start out in terms of neural circuits? Is it just a soup of nerve cells, with random connections?
        - My guess is the standard circuits (smell, controlling body function, (pain, pleasure, heat, etc.), auditory/visual circuits) are present in everyone, in standard form. The rest develop with feedback from environment.
- 
- ## Effects of Psychoactives
    - Psychedelics, anti-depressants, stimulants, sedatives, etc. Anything that changes how the brain functions.
    - I wonder what we'd find if Hunter S. Thomson had a portable f-MRI machine on his head as he went about his drug frenzies.
        - Guy took almost every drug known to humankind: adrenochrome, LSD, cannabis, ether, heroin, cocaine, nicotine, EHHH, I don't even know how many he took.
        - A single person, taking different chemicals, in a controlled environment. So we can ignore differences across persons.
    - What can we expect to learn from this?
        - Relating the outward effects: confidence, aggression, sedation, creativity, etc. with inner neural firing patterns / population dynamics / fMRI signals. Find common patterns.
- 
- ## Sleep and Dreams
    - Hippocampal replay during sleep.
        - Same sequences of neural activations that happened during waking, but faster. Replaying memories to form patterns?
    - Repair, memory consolidation, unconscious problem solving.
    - [[Sleep and Dreams - References]]
- 
- ## Can we inject properties we think are good?
    - Prediction ability, resistance to biases, not buckling under pressure, mental strength, confidence, ethics. Can we inject that into any brain? Or would it take a complete overhaul of the complete circuit?
- 
- ## Continuous brain monitoring
    - Neuralink-like, higher accuracy read/write devices that we can play with.
- 
- ## Algorithmic bounds/barriers
    - It's inherently infeasible to properly understand large enough neural nets.
        - Understand: know behaviour for possible inputs
        - Since possible states the brain might be in grows exponentially.
        - Paper: [Algorithmic barrier to neural circuit understanding](https://www.biorxiv.org/content/10.1101/639724v1.full)
        - Distill article on neural network circuits - READ
    - Brains are plastic (for large organisms). So understanding can't be gained from experimenting on one organism (human or otherwise) due to continuous changing. Simulation can overcome this.
    - Do we __need__ to understand brains in such detail? Can we use abstractions or higher level descriptions instead? Things like tendencies, personality, etc.
        - Like in Diaspora, the womb explored the digital genome mapping out gene variations to outward effects on cognition, and every once in a while would create an entirely new, unexplored being. Maybe this kind of __exploration__ is needed instead of complete understanding.
- 
- ## RL
    - Is RL an accurate model for intelligent agents?
- 
- ## Grand unifiying theory of cognition?
    - Neuro people have collected loads of data that makes local progress, but nobody seems to be working on a grand unifying theory of cognition.
    - Looks like people have basically fleshed out the visual part as a single thing, but too few people looking at how it helps and is helped by other regions. Same for auditory.
- 
- ## Human Brain Project / Blue Brain Project
- 
- # Questions
    - Confusion points
        - **neurons are chaotic** (small diff in initial conditions make large differences in outcomes). Then how come collections of neurons (brains) tend to create smoothed behaviour?
            - Is the continuous time-stepping important, or would coarse computation be enough? keep in mind the butterfly effect
        - **neurons (cerebellum) >> neurons (cerebrum)**. How does this make sense?
- 
- 
- __I hope to be around
the day we grasp, in truth,
the nature of mind.
Befriending time, in truth__
- #WIP #blog #neuroscience

