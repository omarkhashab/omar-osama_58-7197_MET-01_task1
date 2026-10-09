# Club Sign-ups Data Cleaning

**Name:** Omar Khashab  
**Student ID:** 58-7197

## Part C — Cleaning Explanation

The original dataset contained 39 sign-up submissions with inconsistent values and duplicate records. I first inspected the dataset using `shape`, `dtypes`, and `value_counts()` to identify the problems. I then standardized faculty, club, and city values by removing extra spaces, converting text to lowercase, and applying mapping dictionaries to obtain the required canonical values. For example, "Soccer" became "Football", and "Media Engineering and Technology" became "MET". I also standardized names by removing extra spaces and applying title case, and converted emails to lowercase. Payment values such as "yes", "Y", and "1" were converted into Boolean values. The two date formats were parsed into a single datetime column, correctly interpreting slash-separated dates as day/month/year.

After cleaning, I removed 3 exact duplicate rows, reducing the dataset from 39 to 36 rows. I then removed 4 repeated student-club registrations, keeping the latest submission because students may have updated their payment status. This left 32 unique student-club registrations.

Cleaning order mattered: checking repeated registrations before standardizing club names identified only 2 duplicates, compared with 4 after standardization. Finally, I used `student_id` and `club` instead of names to identify duplicates, avoiding accidental merging of different students who shared the same name.