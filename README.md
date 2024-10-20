# AI-Powered-Personalized-Meal-Planner-for-Balanced-Nutrition-and-Health

```Python
import pandas as pd

# Final comprehensive dataset with various categories and health-specific foods
data = [
    # Tamil Nadu Dishes
    ["Idli Sambar", "Rice Batter, Lentils, Spices", 150, 8, 30, 2, "Vegan", "Weight Loss", "Breakfast", 15],
    ["Pongal", "Rice, Moong Dal, Ghee, Spices", 300, 10, 45, 10, "Vegetarian", "Weight Gain", "Breakfast", 20],
    ["Curd Rice", "Rice, Curd, Green Chilies, Curry Leaves", 180, 5, 30, 5, "Vegetarian", "Maintenance", "Main Course", 10],
    ["Sambar Rice", "Rice, Lentils, Spices", 200, 8, 40, 2, "Vegan", "Weight Loss", "Main Course", 15],
    ["Rasam", "Tamarind, Tomatoes, Spices", 80, 3, 12, 1, "Vegan", "Weight Loss", "Side Dish", 5],
    ["Puli Sadam", "Rice, Tamarind, Spices", 250, 4, 40, 5, "Vegan", "Maintenance", "Main Course", 10],
    ["Upma", "Rava, Vegetables, Spices", 180, 6, 30, 5, "Vegan", "Weight Loss", "Breakfast", 10],
    ["Vadai", "Urad Dal, Spices", 250, 10, 20, 15, "Vegan", "Maintenance", "Snack", 20],
    ["Kuzhi Paniyaram", "Rice Batter, Spices, Onions", 200, 7, 35, 5, "Vegan", "Maintenance", "Snack", 15],
    ["Vegetable Kurma", "Mixed Vegetables, Coconut, Spices", 220, 5, 20, 10, "Vegan", "Maintenance", "Main Course", 25],
    ["Appam", "Rice Batter, Coconut Milk", 180, 3, 35, 5, "Vegan", "Maintenance", "Breakfast", 15],
    ["Chicken Chettinad", "Chicken, Spices, Coconut", 400, 30, 5, 20, "Non-Vegetarian", "Weight Gain", "Main Course", 35],
    ["Mutton Biryani", "Rice, Mutton, Spices", 600, 28, 70, 25, "Non-Vegetarian", "Weight Gain", "Main Course", 40],
    ["Payasam", "Vermicelli, Milk, Sugar, Ghee", 250, 6, 35, 10, "Vegetarian", "Weight Gain", "Dessert", 30],

    # Salads
    ["Cucumber Salad", "Cucumber, Lemon, Salt, Pepper", 50, 1, 12, 0, "Vegan", "Weight Loss","Salad", 5],
    ["Greek Salad", "Cucumber, Tomatoes, Feta, Olives", 120, 5, 15, 8, "Vegetarian", "Maintenance","Salad", 10],
    ["Chickpea Salad", "Chickpeas, Onion, Tomato, Lemon", 220, 12, 30, 6, "Vegan", "Weight Loss", "Salad", 10],

    # Keto Meals
    ["Keto Paneer", "Paneer, Cream, Butter", 350, 18, 6, 30, "Vegetarian", "Keto", "Main Course", 20],
    ["Keto Chicken Salad", "Chicken, Lettuce, Avocado, Olives", 400, 25, 5, 30, "Non-Vegetarian", "Keto", "Salad", 15],
    ["Keto Egg Bhurji", "Eggs, Butter, Spices", 300, 15, 2, 28, "Non-Vegetarian", "Keto", "Breakfast", 10],

    # Diet Foods
    ["Oats Porridge", "Oats, Milk, Honey, Fruits", 150, 5, 25, 4, "Vegetarian", "Diet", "Breakfast", 10],
    ["Quinoa Salad", "Quinoa, Vegetables, Olive Oil", 200, 8, 30, 6, "Vegan", "Diet", "Salad", 15],
    ["Vegetable Stir Fry", "Mixed Vegetables, Olive Oil, Soy Sauce", 180, 5, 15, 7, "Vegan", "Main Course", 20],
    ["Cucumber Salad", "Cucumber, Lemon, Salt, Pepper", 50, 1, 12, 0, "Vegan", "Weight Loss", "Salad", 5],
    ["Greek Salad", "Cucumber, Tomatoes, Feta, Olives", 120, 5, 15, 8, "Vegetarian", "Maintenance","Salad", 10],
    ["Chickpea Salad", "Chickpeas, Onion, Tomato, Lemon", 220, 12, 30, 6, "Vegan", "Weight Loss", "Salad", 10],

    # Diabetes-Friendly Foods
    ["Bitter Gourd Stir Fry", "Bitter Gourd, Spices", 80, 2, 15, 1, "Vegan", "Diabetes", "Side Dish", 10],
    ["Multi-Grain Roti", "Wheat, Millet, Oats", 120, 5, 25, 2, "Vegan", "Diabetes", "Main Course", 15],
    ["Green Moong Dal", "Green Moong Dal, Spices", 180, 12, 25, 3, "Vegan", "Diabetes", "Main Course", 20],
    ["Tomato Rice", "Rice, Tomato, Spices", 200, 10, 40, 3, "Vegan", "Diabetes", "Lunch", 20],
    ["Vegetable Stir Fry", "Rice, Mixed Vegetables", 180, 8, 35, 2, "Vegan", "Diabetes", "Dinner", 20],
    ["Onion and Tomato Curry", "Onion, Tomato, Spices", 160, 7, 25, 2, "Vegan", "Diabetes", "Dinner", 15],
    ["Tomato and Onion Salad", "Tomato, Onion, Cucumber", 80, 3, 10, 0, "Vegan", "Diabetes", "Snack", 10],

    # Blood Pressure-Friendly Foods
    ["Steamed Vegetables", "Broccoli, Carrot, Beans", 90, 4, 10, 1, "Vegan", "BP", "Side Dish", 10],
    ["Brown Rice", "Brown Rice, Salt", 200, 4, 45, 2, "Vegan", "BP", "Main Course", 20],
    ["Beetroot Juice", "Beetroot, Lemon", 80, 2, 18, 0, "Vegan", "BP", "Drink", 5],

    # Heart Health-Friendly Foods
    ["Avocado Toast", "Whole Wheat Bread, Avocado", 250, 5, 30, 12, "Vegan", "Heart Health", "Breakfast", 10],
    ["Grilled Salmon", "Salmon, Spices, Olive Oil", 400, 30, 0, 20, "Non-Vegetarian", "Heart Health", "Main Course", 25],
    ["Mixed Berry Smoothie", "Berries, Yogurt, Chia Seeds", 180, 6, 30, 5, "Vegetarian", "Heart Health", "Drink", 8],
    ["Brown Rice Salad", "Brown rice, cherry tomatoes, cucumbers, bell peppers, red onion, lemon juice, olive oil, herbs", 300, 8, 55, 10, "Vegan", "Weight Loss", "Side Dish", 15],
    ["Vegetable Stir-Fry with Quinoa and Brown Rice", "Quinoa, brown rice, assorted vegetables, low-sodium soy sauce, garlic, ginger", 350, 10, 60, 8, "Vegan", "Maintenance", "Main Course", 25],
    ["Rice and Lentil Bowl", "Brown rice, lentils, sautéed spinach, diced tomatoes, spices", 400, 15, 70, 12, "Vegan", "Maintenance", "Main Course", 30],
    ["Mediterranean Rice Bowl", "Brown rice, chickpeas, olives, diced tomatoes, cucumbers, dressing", 350, 12, 50, 10, "Vegan", "Weight Loss", "Main Course", 20],
    ["Coconut Rice with Mango", "Brown rice, light coconut milk, fresh mango, coconut flakes", 300, 5, 50, 8, "Vegan", "Maintenance", "Dessert", 15],
    ["Stuffed Bell Peppers with Rice and Black Beans", "Bell peppers, brown rice, black beans, corn, spices", 400, 10, 65, 12, "Vegan", "Weight Loss", "Main Course", 30],
    ["Rice Porridge (Congee)", "Brown rice, water or broth, green onions, shredded chicken", 250, 4, 45, 5, "Non-Vegan", "Maintenance", "Breakfast", 25],
    ["Rice and Vegetable Soup", "Brown rice, vegetable broth, assorted vegetables, spices", 200, 3, 40, 5, "Vegan", "Weight Loss", "Starter", 20],

    # Additional Indian Dishes
    ["Masala Dosa", "Rice Batter, Potato, Spices, Ghee", 250, 6, 45, 5, "Vegan", "Maintenance", "Main Course", 20],
    ["Roti with Dal", "Wheat Flour, Lentils, Spices", 220, 10, 35, 3, "Vegan", "Maintenance", "Main Course", 15],
    ["Butter Chicken", "Chicken, Butter, Cream, Spices", 490, 25, 10, 35, "Non-Vegetarian", "Weight Gain", "Main Course", 30],
    ["Palak Paneer", "Spinach, Paneer, Spices", 200, 12, 10, 8, "Vegetarian", "Maintenance", "Main Course", 20],
    ["Aloo Paratha", "Wheat Flour, Potato, Ghee, Spices", 290, 8, 50, 12, "Vegetarian", "Weight Gain", "Breakfast", 15],
    ["Chole Bhature", "Chickpeas, Maida, Spices", 450, 15, 60, 18, "Vegan", "Weight Gain", "Main Course", 25],
    ["Biryani", "Rice, Spices, Meat, Yogurt", 550, 20, 65, 25, "Non-Vegetarian", "Weight Gain", "Main Course", 40],
    ["Upma", "Rava, Vegetables, Spices", 180, 6, 30, 5, "Vegan", "Weight Loss", "Breakfast", 10],
    ["Rajma Chawal", "Kidney Beans, Rice, Spices", 320, 12, 55, 8, "Vegan", "Maintenance", "Main Course", 30],
    ["Paneer Butter Masala", "Paneer, Butter, Cream, Spices", 400, 15, 20, 30, "Vegetarian", "Weight Gain", "Main Course", 25],
    ["Dhokla", "Gram Flour, Spices", 150, 8, 25, 3, "Vegan", "Weight Loss", "Starter", 20],
    ["Kheer", "Rice, Milk, Sugar", 250, 6, 35, 8, "Vegetarian", "Weight Gain", "Dessert", 30],
    ["Poha", "Flattened Rice, Vegetables, Spices", 180, 5, 30, 4, "Vegan", "Weight Loss", "Breakfast", 10],
    ["Chicken Tikka", "Chicken, Spices, Yogurt", 290, 25, 5, 15, "Non-Vegetarian", "Maintenance", "Starter", 20],
    ["Matar Paneer", "Paneer, Peas, Spices", 250, 14, 15, 12, "Vegetarian", "Maintenance", "Main Course", 25],
    ["Gajar Halwa", "Carrot, Milk, Ghee, Sugar", 300, 5, 35, 15, "Vegetarian", "Weight Gain", "Dessert", 40],
    ["Pesarattu", "Green Gram, Spices", 200, 10, 25, 4, "Vegan", "Weight Loss", "Breakfast", 15],
    ["Fish Curry", "Fish, Spices, Coconut Milk", 350, 25, 5, 20, "Non-Vegetarian", "Weight Gain", "Main Course", 25],
    ["Vada Pav", "Potato, Bread, Spices", 280, 5, 40, 10, "Vegan", "Weight Gain", "Snack", 10],
    ["Rasgulla", "Paneer, Sugar Syrup", 150, 4, 30, 2, "Vegetarian", "Weight Gain", "Dessert", 20],
    ["Sambar Rice", "Rice, Lentils, Spices", 200, 8, 40, 2, "Vegan", "Weight Loss", "Main Course", 15],
    ["Bhindi Masala", "Okra, Spices, Oil", 120, 3, 10, 7, "Vegan", "Weight Loss", "Main Course", 20],
    ["Hyderabadi Biryani", "Rice, Meat, Spices, Yogurt", 600, 28, 70, 25, "Non-Vegetarian", "Weight Gain", "Main Course", 45],

    ["Oatmeal", "Oats, Milk, Honey, Banana", 150, 5, 27, 3, "Vegetarian", "Weight Loss", "Main Course", 10],
    ["Grilled Chicken", "Chicken, Olive Oil, Spices", 300, 30, 0, 15, "Non-Vegetarian", "Weight Gain", "Main Course", 20],
    ["Green Smoothie", "Spinach, Apple, Banana, Water", 180, 2, 40, 0.5, "Vegan", "Weight Loss", "Starter", 5],
    ["Paneer Tikka", "Paneer, Spices, Yogurt", 250, 14, 10, 12, "Vegetarian", "Maintenance", "Starter", 15],
    ["Chocolate Cake", "Flour, Cocoa, Sugar, Eggs", 450, 6, 60, 20, "Vegetarian", "Weight Gain", "Dessert", 30],
    ["Butter Chicken", "Chicken, Butter, Cream, Spices", 490, 25, 10, 35, "Non-Vegetarian", "Weight Gain", "Main Course", 30],
    ["Avocado Toast", "Bread, Avocado, Olive Oil", 220, 4, 30, 10, "Vegan", "Maintenance", "Main Course", 10],
    ["Fish Curry", "Fish, Spices, Coconut Milk", 350, 25, 5, 20, "Non-Vegetarian", "Weight Gain", "Main Course", 25],
    ["Fruit Salad", "Apple, Orange, Berries", 120, 1, 30, 0.5, "Vegan", "Weight Loss", "Dessert", 5],
    ["Mango Smoothie", "Mango, Yogurt, Honey", 200, 5, 35, 3, "Vegetarian", "Weight Loss", "Starter", 5],
    ["Egg Salad", "Eggs, Lettuce, Mayo", 300, 10, 2, 25, "Non-Vegetarian", "Maintenance", "Starter", 10],
    ["Vegetable Soup", "Carrot, Tomato, Onion, Spices", 90, 2, 15, 1, "Vegan", "Weight Loss", "Starter", 20],
    ["Chia Pudding", "Chia Seeds, Almond Milk, Honey", 180, 6, 20, 8, "Vegan", "Weight Loss", "Dessert", 10],
    ["Pasta Alfredo", "Pasta, Cream, Cheese, Garlic", 550, 12, 60, 25, "Vegetarian", "Weight Gain", "Main Course", 30],
    ["Mutton Biryani", "Rice, Mutton, Spices, Ghee", 600, 28, 70, 25, "Non-Vegetarian", "Weight Gain", "Main Course", 40],
    ["Quinoa Salad", "Quinoa, Cucumber, Tomato, Olive Oil", 150, 4, 25, 5, "Vegan", "Maintenance", "Main Course", 10],
    ["Chicken Wrap", "Chicken, Tortilla, Veggies, Mayo", 320, 20, 30, 15, "Non-Vegetarian", "Weight Gain", "Main Course", 15],
    ["Veggie Stir-fry", "Bell Peppers, Broccoli, Tofu, Soy Sauce", 200, 12, 18, 7, "Vegan", "Weight Loss", "Main Course", 15],
    ["Ice Cream", "Milk, Sugar, Cream", 250, 4, 20, 15, "Vegetarian", "Maintenance", "Dessert", 5],
    ["Falafel Wrap", "Chickpeas, Spices, Tortilla", 300, 10, 35, 10, "Vegan", "Maintenance", "Main Course", 20],
    ["Sushi", "Rice, Fish, Seaweed", 400, 15, 50, 5, "Non-Vegetarian", "Maintenance", "Main Course", 30],
    ["Greek Salad", "Cucumber, Tomato, Feta, Olive Oil", 180, 5, 10, 12, "Vegetarian", "Weight Loss", "Starter", 10],
    ["Tofu Scramble", "Tofu, Spinach, Spices", 200, 15, 10, 5, "Vegan", "Weight Loss", "Main Course", 15],
    ["Peanut Butter Sandwich", "Bread, Peanut Butter", 300, 8, 40, 12, "Vegetarian", "Weight Gain", "Main Course", 5],
    ["Brownie", "Flour, Cocoa, Butter, Sugar", 450, 5, 55, 20, "Vegetarian", "Weight Gain", "Dessert", 25],
    ["Lentil Soup", "Lentils, Onion, Carrot, Spices", 180, 12, 25, 3, "Vegan", "Maintenance", "Starter", 20],
    ["Chicken Caesar Salad", "Chicken, Lettuce, Parmesan", 320, 25, 5, 20, "Non-Vegetarian", "Maintenance", "Starter", 15],
    ["Porridge", "Oats, Milk, Berries", 160, 6, 30, 4, "Vegetarian", "Weight Loss", "Main Course", 10],
    ["Masala Dosa", "Rice Batter, Potato, Spices", 250, 6, 45, 5, "Vegan", "Maintenance", "Main Course", 20],

    #dietary_restrictions
    #["Heart Health", "mutton", "beef", "pork", "butter"],
    #["Diabetes", "sugar", "white bread", "syrups"],
    #["Weight Loss", "sugary drinks", "fried foods"]
]

columns = ["Meal_Name", "Ingredients", "Calories (kcal)", "Protein (g)", "Carbs (g)", "Fats (g)", "Diet_Type", "Goal", "Course", "Prep_Time (mins)"]
df = pd.DataFrame(data, columns=columns)
csv_path = "overall_food_dataset.csv"
df.to_csv(csv_path, index=False)
print(f"Dataset saved at: {csv_path}")


import pandas as pd
from fuzzywuzzy import fuzz

# Load the dataset
df = pd.read_csv("overall_food_dataset.csv")

def recommend_meals(available_ingredients, goal):
    """
    Recommends meals based on available ingredients and the user's goal.
    Uses fuzzy matching and fallback options for minimal input.
    """
    # Filter meals based on the dietary goal
    filtered_meals = df[df["Goal"].str.contains(goal, case=False)]

    # Print filtered meals for debugging
    print("Filtered Meals for Goal:", filtered_meals[['Meal_Name', 'Goal']])

    # Store matching recommendations
    recommendations = set()

    # Use fuzzy matching to match the ingredients
    for _, row in filtered_meals.iterrows():
        meal_ingredients = row["Ingredients"].lower().split(", ")
        match_count = sum(
            fuzz.partial_ratio(ingredient.lower(), meal_ingredient) > 70  # Adjusted threshold
            for ingredient in available_ingredients
            for meal_ingredient in meal_ingredients
        )

        # Recommend meals that have at least two strong matches
        if match_count >= 2:
            recommendations.add(row["Meal_Name"])

    # If no recommendations found, provide a fallback
    if not recommendations:
        recommendations = fallback_recommendations(goal)

    return list(recommendations)

def fallback_recommendations(goal):
    """
    Provides fallback recommendations based on the goal if no exact matches are found.
    """
    fallback_meals = df[df["Goal"].str.contains(goal, case=False)]["Meal_Name"].tolist()
    if not fallback_meals:
        fallback_meals = ["Salad Bowl", "Fruit Bowl", "Smoothie"]
    return fallback_meals

def calculate_accuracy(recommendations, expected_meals):
    """
    Calculates the accuracy of the recommendations.
    """
    if not expected_meals:
        return 0.0
    matches = len(set(recommendations) & set(expected_meals))
    accuracy = (matches / len(expected_meals)) * 100
    return accuracy

def main():
    print("Welcome to the Enhanced Meal Recommendation System!")

    # User inputs available ingredients
    ingredients = input("Enter the ingredients you have at home (comma-separated): ").split(",")
    ingredients = [ingredient.strip() for ingredient in ingredients]

    # User selects a dietary goal
    print("\nChoose your dietary goal:")
    print("1. Weight Loss\n2. Weight Gain\n3. Diabetes\n4. Blood Pressure\n5. Heart Health\n6. Diet")
    goal_choice = input("Enter the number corresponding to your goal: ").strip()

    # Map the user's choice to goal string
    goal_mapping = {
        "1": "Weight Loss",
        "2": "Weight Gain",
        "3": "Diabetes",
        "4": "BP",
        "5": "Heart Health",
        "6": "Diet"
    }
    goal = goal_mapping.get(goal_choice, "")

    if not goal:
        print("Invalid choice. Please try again.")
        return

    # Get meal recommendations
    recommendations = recommend_meals(ingredients, goal)

    # Display the recommendations
    print("\nRecommended Meals:")
    for meal in recommendations:
        print(f"- {meal}")

    # Expected meals for testing
    expected_meals = {
        "Weight Gain": ['Payasam', 'Kheer', 'Gajar Halwa'],
        "Weight Loss": ['Cucumber Salad', 'Chickpea Salad'],
        "Diabetes": ['Grilled Chicken'],
        "Heart Health": ['Vegetable Soup'],
        "Diet": ['Brownie']
    }.get(goal, [])

    # Calculate and print accuracy
    accuracy = calculate_accuracy(recommendations, expected_meals)
    print(f"Accuracy of the recommendation system: {accuracy:.2f}%")

def test_recommendations():
    """
    Tests the recommendation system with predefined ingredients and goals.
    """
    test_cases = [
        (["milk", "sugar"], "Weight Gain", ['Payasam', 'Kheer', 'Gajar Halwa']),
        (["spinach", "tomato"], "Weight Loss", ['Cucumber Salad', 'Chickpea Salad']),
        (["chicken", "rice"], "Diabetes", ['Grilled Chicken']),
        (["broccoli"], "Heart Health", ['Vegetable Soup']),
        (["flour"], "Diet", ['Brownie']),
    ]

    for ingredients, goal, expected in test_cases:
        print(f"\nTesting with ingredients: {ingredients} and goal: {goal}")
        recommendations = recommend_meals(ingredients, goal)
        print("Recommended Meals:", recommendations)
        accuracy = calculate_accuracy(recommendations, expected)
        print(f"Expected Meals: {expected}, Matches Found: {len(set(recommendations) & set(expected))}")
        print(f"Accuracy: {accuracy:.2f}%")

if __name__ == "__main__":
    main()
    # Uncomment the line below to run tests
    # test_recommendations()


```
