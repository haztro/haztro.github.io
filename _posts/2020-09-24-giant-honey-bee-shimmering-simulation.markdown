---
layout: post
title:  "Giant Honey Bee Shimmering Simulation"
---

I'm fascinated by the way giant honey bees coordinate with each other to create this super cool *wave*/*shimmer* effect. Check them out in action [**here**](https://www.youtube.com/watch?v=8bNKU8GRYmU&t). They raise their abdomens in concert to create these wave-like patterns that ward off predators. I thought it'd be interesting to try and replicate the effect by simulating it, and maybe turn it into some sort of interactive thing.  

I started by drawing a little bee to make testing a bit more interesting: 

![image tooltip here](/assets/giant-honey-bee/bee.png)

I used Godot for the simulation. First I wrote some code that generates a bunch of bees all in a grid. To allow communication amongst the bees, each bee has the ability to send a "shimmer signal" to each of its 8 neighbouring bees.

![image tooltip here](/assets/giant-honey-bee/bee_grid.jpg)

Before moving on I made the "bee grid" look a little more natural by randomly offsetting the bees, adding some little animations and giving them a background. This makes for a pretty  neat looking hive. 

![image tooltip here](/assets/giant-honey-bee/flap.gif)
![image tooltip here](/assets/giant-honey-bee/wiggle.gif)
![image tooltip here](/assets/giant-honey-bee/shim.gif)

![image tooltip here](/assets/giant-honey-bee/bee_grid_1.jpg)

I tried to keep the implementation for the shimmer behaviour as simple as possible. After spending a bunch of time carefully watching the bees do their thing, I came up with four parameters that I thought would reasonably capture the effect: 

- shimmer threshold / wave strength,
- wave propagation,
- wave decay,
- shimmer cooldown.

The bees will only shimmer if the **wave strength** exceeds their shimmer threshold. This parameter makes it possible to have shimmer bouts that recruit a varying number of bees depending on the wave strength - it also effects the duration of the wave. A bee receives and accumulates shimmer signals from multiple bees during the wave propagation delay.
**Wave propagation** is the speed at which the bees can communicate information. This limits the speed of the "waves". **Wave decay** controls the speed at which the wave strength decreases. Each time a bee passes on the shimmer signal, the wave strength decays. **Shimmer cooldown** is the time it takes a bee to recover after performing an abdomen raise. The implication of this is that a bee can't shimmer if it is shimmering already. Below is pseudocode for the shimmer behaviour.

``` javascript
func shimmer(wave_strength):
    if can_shimmer and wave_strength >= shimmer_threshold:
        can_shimmer = false
        // send signal to neighbouring bees with slightly weaker wave strength.
        emit_signal("shimmer", wave_strength - shimmer_decay)       
        start_cooldown_timer()

func received_shimmer_signal(wave_strength):
    if start_propagation_delay_timer is stopped:
        // With each shimmer signal received from neighbouring bees we increase the wave_strength.
        wave_strength_accumulated = wave_strength + rand_range(0, grow_rate)      
        // Make the delay time a function of the wave_strength  
        propagation_delay.wait_time = max((1 - wave_strength_accumulated), 0) * time_scale + min_delay_time
        start_propagation_delay_timer()

func propagation_delay_timeout():
    shimmer(wave_strength_accumulated)

func cooldown_timeout():
    can_shimmer = true
    wave_strength_accumulated = 0
```

After a lot of trial and error I eventually arrived at this: 

![image tooltip here](/assets/giant-honey-bee/bees.gif)

Close enough for me... Everything here was just clumsily put together after watching [**this**](https://www.youtube.com/watch?v=8bNKU8GRYmU&t) video over and over again. If anyone knows of some actual research done on this behaviour, I'd love to hear about it :)

I finished it off by adding some sound effects. You can mess around with it yourself on [**itch.io**](https://haztro.itch.io/bee-toy).

<iframe style="max-width: 100%" frameborder="0" src="https://itch.io/embed/988109" width="552" height="167"><a href="https://haztro.itch.io/bee-toy">Bee Toy by haztro</a></iframe>
