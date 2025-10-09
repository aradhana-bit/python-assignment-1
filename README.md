# python-assignment-1

# ============================================================
# Project Title : Daily Calorie Tracker (CLI App)
# Author        : S Aradhana
# Course        : Programming for Problem Solving using Python
# ============================================================
# Description:
# This simple Command-Line Application allows users to track
# their daily calorie intake by logging their meals and calorie
# counts. It calculates total and average calories, compares
# them against a daily limit, and optionally saves a report.
# ============================================================

from datetime import datetime

# -------------------------------
# Task 1: Setup & Introduction
# -------------------------------
print("=" * 60)
print("🍎  WELCOME TO YOUR DAILY CALORIE TRACKER  🍎")
print("=" * 60)
print("Hi there! 👋 This tool helps you keep an eye on what you eat today.")
print("You’ll enter your meals, record their calories, and get a full report.\n")

# -------------------------------
# Task 2: Input & Data Collection
# -------------------------------
meals = []
calories = []

try:
    num_meals = int(input("👉 How many meals or snacks did you have today? "))
    print()

    for i in range(num_meals):
        print(f"--- Meal {i+1} ---")
        meal_name = input("Enter meal name (e.g., Breakfast, Lunch): ").strip().title()
        calorie_value = float(input(f"Enter calories for {meal_name}: "))
        meals.append(meal_name)
        calories.append(calorie_value)
        print("Meal added successfully ✅\n")

except ValueError:
    print("⚠  Invalid input detected! Please restart and enter valid numbers only.")
    exit()

# -------------------------------
# Task 3: Calorie Calculations
# -------------------------------
total_calories = sum(calories)
average_calories = total_calories / len(calories)

# Ask user for daily limit
daily_limit = float(input("💪 What’s your personal daily calorie limit? "))

# -------------------------------
# Task 4: Exceed Limit Warning System
# -------------------------------
if total_calories > daily_limit:
    status_message = "⚠ Oh no! You’ve exceeded your daily calorie limit. Time to slow down a bit!"
else:
    status_message = "✅ Awesome! You’re within your calorie limit. Keep it up!"

# -------------------------------
# Task 5: Neatly Formatted Output
# -------------------------------
print("\n" + "=" * 60)
print("📊  DAILY CALORIE SUMMARY REPORT")
print("=" * 60)
print(f"{'Meal Name':<25}{'Calories':>10}")
print("-" * 40)

for meal, cal in zip(meals, calories):
    print(f"{meal:<25}{cal:>10.2f}")

print("-" * 40)
print(f"{'Total Calories:':<25}{total_calories:>10.2f}")
print(f"{'Average per Meal:':<25}{average_calories:>10.2f}")
print("=" * 60)
print(status_message)
print("=" * 60)

