#This is an Iranian Python code for people who want to use solar dates in their codes and programs
class PersianCalendar:
    def __init__(self, year, month, day):
        self.year = year
        self.month = month
        self.day = day

    def to_gregorian(self):
        """تبدیل تاریخ شمسی به تاریخ میلادی"""
        g_year = self.year + 621
        g_month = (self.month - 1) * 3 + 1
        if self.year > 0 and self.month >= 10:
            g_month += 1
        g_day = self.day
        if g_month > 12:
            g_year += 1
            g_month -= 12
        return g_year, g_month, g_day

    def to_persian(self, g_year, g_month, g_day):
        """تبدیل تاریخ میلادی به تاریخ شمسی"""
        p_year = g_year - 621
        p_month = (g_month - 1) // 3 + 1
        p_day = g_day
        if g_month > 12:
            p_year += 1
            p_month -= 12
        if (p_year % 33) % 4 == 0 or (p_year % 33) % 4 == 1 or p_year % 33 == 5:
            if p_month == 12 and p_day > 10:
                p_year += 1
                p_month = 1
                p_day -= 10
        return p_year, p_month, p_day

    def __str__(self):
        return f"{self.year:04}/{self.month:02}/{self.day:02}"
#this is just a EZ exampel for Solar date/ you can use this in your python Codes
