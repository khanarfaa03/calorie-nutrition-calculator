# Calorie & Nutrition Calculator

A Python tool built to process nutritional data and calculate total calories, sugars, fats, and other key macronutrients based on custom user inputs.

## 📖 Overview
As part of a feature enhancement for a Health & Leisure application, this project processes nutritional information provided per **100 grams** of various food items (`nutrition.json`). The tool computes total nutritional breakdowns dynamically depending on consumed quantities.

## 📊 Dataset Structure
The project utilizes `nutrition.json` (loaded into `nutrition_dict`), containing key metrics for various foods:

| Key / Column | Description |
| :--- | :--- |
| `food` | The name of the food item |
| *Nutrients* | Nutritional metrics evaluated per 100g serving |

## 🚀 Key Features
* Parses JSON nutritional datasets into native Python dictionaries (`nutrition_dict`).
* Calculates total calories, sugars, fats, and other metrics based on food quantity inputs.
* Modular design suitable for integration into broader health and fitness tracking apps.

## 🛠️ Usage Example

```python
# Sample logic for calculating nutritional values
def calculate_nutrition(food_item, weight_in_grams, nutrition_dict):
    if food_item in nutrition_dict:
        factor = weight_in_grams / 100.0
        item_data = nutrition_dict[food_item]
        
        totals = {
            nutrient: val * factor 
            for nutrient, val in item_data.items() 
            if isinstance(val, (int, float))
        }
        return totals
    else:
        raise ValueError("Food item not found in dataset.")
