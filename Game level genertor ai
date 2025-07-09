import streamlit as st
import random
import numpy as np
import matplotlib.pyplot as plt

# Define tile types
TILE_TYPES = {
    0: "🟩",  # Grass
    1: "🌊",  # Water
    2: "🪨",  # Rock
    3: "🌳",  # Tree
    4: "🔥",  # Lava
}

def generate_level(width, height, difficulty):
    level = np.zeros((height, width), dtype=int)
    for y in range(height):
        for x in range(width):
            # Randomly assign tile based on difficulty
            tile_prob = random.random()
            if tile_prob < difficulty * 0.1:
                level[y][x] = random.choice([2, 3, 4])  # Hard tiles
            elif tile_prob < 0.5:
                level[y][x] = 1  # Water
            else:
                level[y][x] = 0  # Grass
    return level

def render_level(level):
    rendered = ""
    for row in level:
        rendered += "".join([TILE_TYPES[tile] for tile in row]) + "\n"
    return rendered

# Streamlit UI
st.title("🎮 Game Level Generator")
st.write("Create a randomized tile-based game level with emojis!")

cols = st.columns(3)
width = cols[0].slider("Width", 5, 30, 10)
height = cols[1].slider("Height", 5, 30, 10)
difficulty = cols[2].slider("Difficulty", 0.0, 1.0, 0.3)

if st.button("🔁 Generate New Level"):
    level = generate_level(width, height, difficulty)
    st.text(render_level(level))
