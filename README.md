public class Date1 {
	

	private int day; 			
	private int month;
	private int year;
	
	private static int [] daysPerMonth = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}; 
	
	
	public Date1(){
		this.day = 1;
		this.month = 1;
		this.year = 1900;	
	}
	
	public Date1(int day, int month, int year){
		this.day = day;
		this.month = month;
		this.year = year;
	}
	
	public Date1(Date1 date){
		this.day = date.day;
		this.month = date.month;
		this.year = date.year;
	}

	
	public String toString(){
		return formatValue(day) + "." + formatValue(month) + "." + formatValue(year);
	}
	public void incDay(int amount) { 
		if (amount < 0) {
			System.out.println(" 'amount' value should be greater than 0");
			return;
		}
		day += amount; 
		
		shiftDateInc(); 
	}
	
	public void decDay(int amount) {
		if (amount < 0) {
			System.out.println(" 'amount' value should be greater than 0");
			return;
		}
		day -= amount;
		
		shiftDateDec();
	}
	
	
	public static int Diff(Date1 date1, Date1 date2){
		return (date1.year*date1.month + date1.month) - (date2.year*date2.month  + date2.month);
	}
	
	//private methods
	private void shiftDateInc() {
	int numberOfDaysInCurrentMonth = daysPerMonth[month - 1]; //index of the array
		if (day > numberOfDaysInCurrentMonth) {
			day -= numberOfDaysInCurrentMonth;
			++ month;
			if (month > 12) {
				month = 1;
				++ year;
			}
			shiftDateInc(); 
		}
	}
	
	private void shiftDateDec() {
	int	numberOfDaysInCurrentMonth = daysPerMonth[month - 1];
		if (day <= 0) {
			-- month;
			day = numberOfDaysInCurrentMonth + day;
			if (month < 1) {
				month = 12;
				-- year;
			}
			shiftDateDec();
		}
	}

	
	private String formatValue(int value) {
		return value < 10 ? "0" + value : "" + value;
	}
	
	
	//getters and setters
	public int getDay() {
		return day;
	}
	
	public void setDay(int day) {
		this.day = day;
	}
	
	public int getMonth() {
		return month;
	}
	
	public void setMonth(int month) {
		this.month = month;
	}
	
	public int getYear() {
		return year;
	}
	public void setYear(int year) {
		this.year = year;
	}

}
