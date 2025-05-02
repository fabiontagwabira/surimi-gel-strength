# surimi-gel-strength
A food safety calculator for surimi gel strength formulas

# 🧪 Surimi Gel Strength Calculator App

# Step 1: Define product codes and associated formulas
product_codes = {
    '100100': 'Pacific Crab Mix',
    '100200': 'Atlantic Lobster Blend'
}

# Associate each product with a list of surimi formulas
product_formulas = {
    '100100': ['formula_823', 'formula_562'],
    '100200': ['formula_941', 'formula_823', 'formula_562']
}

# Step 2: Define gel strength functions
def formula_823():
    print('\n🔬 Calculate Gel Strength for Formula 823')
    return calculate_gel_strength(required_strength=650, formula_name='823')

def formula_941():
    print('\n🔬 Calculate Gel Strength for Formula 941')
    return calculate_gel_strength(required_strength=700, formula_name='941')

def formula_562():
    print('\n🔬 Calculate Gel Strength for Formula 562')
    return calculate_gel_strength(required_strength=700, formula_name='562')

# Shared calculation logic to avoid repetition
def calculate_gel_strength(required_strength, formula_name):
    gel_A = float(input('Enter gel strength for grade A: '))
    count_A = int(input('Enter count for grade A: '))

    gel_KA = float(input('Enter gel strength for grade KA: '))
    count_KA = int(input('Enter count for grade KA: '))

    gel_RA = float(input('Enter gel strength for grade RA: '))
    count_RA = int(input('Enter count for grade RA: '))

    total_strength = (gel_A * count_A) + (gel_KA * count_KA) + (gel_RA * count_RA)
    total_count = count_A + count_KA + count_RA
    average_strength = total_strength / total_count

    print(f'\n🧾 Average gel strength for formula {formula_name}: {average_strength:.2f}')

    if average_strength >= required_strength:
        print('✅ Gel strength is ACCEPTABLE')
    else:
        print('❌ Gel strength is NOT ACCEPTABLE')

# Step 3: Main program logic
try:
    code = input('\n📦 Enter the UPC: ')
    product = product_codes[code]
    print(f'\n🧾 Product selected: {product}')

    formulas = product_formulas.get(code, [])
    for formula in formulas:
        eval(f"{formula}()")  # Dynamically call the function by name

except KeyError:
    print('\n🚫 Invalid input: UPC not found')
