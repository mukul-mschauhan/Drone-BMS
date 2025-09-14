# Drone Battery Management System (BMS) – Prototype
## Overview

This repository contains a prototype implementation of a Battery Management System (BMS) for drones, built using a hybrid physics + ML approach. It demonstrates how simulated data can be used to bootstrap predictive models for flight time and battery consumption, and provides a Streamlit UI for real-time interaction. 

The goal is to evolve this prototype into a defense-grade mission-aware BMS that can reliably inform soldiers of remaining flight time, safe-to-land windows, and battery risk under varying environmental and mission conditions.

## Features

- **Flight Time Prediction:** Real‑time estimation of remaining flight time (minutes).
- **Battery Consumption Prediction:** Estimate of battery % consumed for mission duration.
- **Environmental Awareness:** Models temperature effects (50°C summer, 0°C cold, snow, rain).
- **Mission Profile Inputs:** Payload (0–5 kg), wind, maneuver aggressiveness, time of day.
- **Subsystem Loads:** LiDAR, thermal camera, RGB camera, and compute modes (Jetson low/med/high).
- **Power Breakdown:** Displays propulsion vs sensors vs compute power contributions.
- **Simulate & Learn:** Generate focused synthetic data around the current operating point and retrain models live.

## Repository Structure

**battery_simulator.py**
Physics‑inspired simulator generating synthetic drone mission datasets. Models propulsion power, battery effective capacity, and subsystem loads.

**data/simulated_drone_battery_dataset_v2.csv**
Example dataset (~4000 missions) generated via the simulator.

**app.py**
Streamlit app providing the BMS UI. Loads data/models, allows predictions, displays breakdowns, and supports real‑time simulation + retraining.

## In the UI
1. Use sidebar controls to set mission parameters (weather, payload, sensors, compute mode, etc.).
2. Click Predict to view:
   - Estimated Flight Time (min)
   - Battery Consumed (%)
   - Power breakdown & usable capacity

3. Use Simulate & Learn to:
   - Generate synthetic batches around the current operating point
   - Retrain the models on new data
   - Update predictions with improved accuracy
  
