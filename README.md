# LinearRegression_1
LinearRegression1 + math2



🔢 הקוד שלך צעד־צעד – הסבר מלא:
📦 ייבוא ספריות:
python
Copy
Edit
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
שורה	הסבר
numpy	לעבודה עם מערכים מתמטיים (כמו אקסלים). נשתמש כדי להגדיר את הנתונים.
matplotlib.pyplot	ספרייה לציור גרפים
LinearRegression	מודל מוכן לרגרסיה ליניארית מתוך scikit-learn

📈 שלב 1: הגדרת הנתונים (x) – השקעה בפרסום
python
Copy
Edit
investment = np.array([10, 15, 20, 25, 30, 35, 40, 45, 50]).reshape(-1, 1)
מרכיב	הסבר
np.array([...])	יוצרים מערך של השקעות באלפי שקלים
.reshape(-1, 1)	הופך את זה לעמודת ערכים – צורת קלט נדרשת למודל LinearRegression

📌 למשל, 10 מייצג 10,000 ש"ח השקעה.

📈 שלב 2: הגדרת התוצאות (y) – גידול במכירות
python
Copy
Edit
sales_growth = np.array([25, 30, 40, 45, 50, 60, 65, 70, 80])
מרכיב	הסבר
מערך פשוט	עבור כל השקעה מהשורה הקודמת, זה הצפי לגידול במכירות

📌 למשל, עבור השקעה של 10,000 ש"ח – נצפה לגידול של 25,000 ש"ח.

⚙️ שלב 3: יצירת אובייקט של מודל רגרסיה ליניארית
python
Copy
Edit
model = LinearRegression()
זה כמו “מכונה” שעוד רגע נכניס לה את הנתונים – והיא תמצא קו שמתאר את הקשר הכי טוב בין השקעה לתוצאה.

🧠 שלב 4: אימון המודל על הנתונים
python
Copy
Edit
model.fit(investment, sales_growth)
המודל לומד את הקשר בין investment ל־sales_growth

מחשב את השיפוע (m) וה־חיתוך עם ציר y (b) כך שהקו יתאים הכי טוב לנתונים

🧮 שלב 5: שליפת ערכי m ו־b
python
Copy
Edit
m = model.coef_[0]
b = model.intercept_
משתנה	הסבר
m	השיפוע של הקו: כמה גדלות המכירות בכל 1000 ש"ח נוספים בפרסום
b	החיתוך עם ציר y: גידול במכירות גם אם לא השקענו בכלל

📝 שלב 6: הצגת משוואת קו הרגרסיה
python
Copy
Edit
equation = f"y = {m:.2f}x + {b:.2f}"
print("Regression Line Equation:", equation)
יוצרים מחרוזת של המשוואה

:.2f מציג 2 ספרות אחרי הנקודה

מדפיסים: לדוגמה y = 1.35x + 11.17

🤖 שלב 7: חיזוי גידול במכירות עבור השקעה של 60K
python
Copy
Edit
x_predict = 60
y_predicted = model.predict([[x_predict]])[0]
print(f"Predicted sales growth for 60K investment: {y_predicted:.2f}K ILS")
שורה	הסבר
x_predict = 60	מציין השקעה של 60,000 ש"ח
model.predict([[x_predict]])	חיזוי ערך y (מכירות) לפי x
[0]	שולף את הערך מתוך המערך שחוזר
print(...)	מדפיס את התחזית (למשל 92.17K ש"ח)

🔍 שלב 8: חיזוי השקעה נדרשת עבור יעד מכירות 100K
python
Copy
Edit
y_target = 100
x_required = (y_target - b) / m
print(f"Investment required for 100K sales growth: {x_required:.2f}K ILS")
משתמשים במשוואה ההפוכה: x = (y - b) / m

מחשבים מה גובה ההשקעה שיביא ל־100,000 ש"ח גידול במכירות

לדוגמה: ≈ 65.80K ש"ח

📊 שלב 9: ציור הגרף
python
Copy
Edit
plt.figure(figsize=(10, 6))  # גודל הגרף
ציור הנתונים המקוריים:
python
Copy
Edit
plt.scatter(investment, sales_growth, color='blue', label='Actual Data')
נקודות כחולות = הנתונים שנתנו במקור

ציור קו הרגרסיה:
python
Copy
Edit
plt.plot(investment, model.predict(investment), color='red', label='Regression Line')
קו אדום = התחזיות של המודל לפי כל x

סימון תחזית (x = 60):
python
Copy
Edit
plt.scatter([x_predict], [y_predicted], color='green', s=100, label='Prediction (x=60)')
נקודה ירוקה: מסמנת את התחזית עבור השקעה של 60K

תוספות גרפיות:
python
Copy
Edit
plt.title("Advertising Investment vs Sales Growth")
plt.xlabel("Investment (Thousands of ILS)")
plt.ylabel("Sales Growth (Thousands of ILS)")
plt.grid(True)
plt.legend()
כותרת, שמות לצירים, רשת רקע, מקרא לגרף

הצגת נוסחת הקו על הגרף:
python
Copy
Edit
plt.text(10, 85, equation, fontsize=12, color='red')
כותב את המשוואה על הגרף באזור x=10, y=85

הצגת הגרף:
python
Copy
Edit
plt.show()
מראה את הגרף כולו

✅ סיכום מה נעשה:
שלב	פעולה
1–2	קלט נתונים (x השקעה, y מכירות)
3–4	בניית מודל ואימון
5–6	חישוב והצגת משוואת הקו
7–8	חיזוי y לפי x, וחיזוי x לפי y
9	ציור גרף מלא עם קו, נקודות, תחזית וכותרות


