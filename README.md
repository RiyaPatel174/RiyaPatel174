- class Appointment:
    def __init__(self, day_of_week="", start_time_hour=0):
        self.client_name = ""
        self.client_phone = ""
        self.appt_type = 0  # 0 represents "Available"
        self.day_of_week = day_of_week
        self.start_time_hour = start_time_hour

    def get_client_name(self):
        return self.client_name

    def get_client_phone(self):
        return self.client_phone

    def get_appt_type(self):
        return self.appt_type

    def get_day_of_week(self):
        return self.day_of_week

    def get_start_time_hour(self):
        return self.start_time_hour

    def get_end_time_hour(self):
        return self.start_time_hour + 1

    def get_appt_type_desc(self):
        type_desc = {
            0: "Available",
            1: "Mens Cut",
            2: "Ladies Cut",
            3: "Mens Colouring",
            4: "Ladies Colouring"
        }
        return type_desc.get(self.appt_type, "Unknown")

    def set_client_name(self, client_name):
        self.client_name = client_name

    def set_client_phone(self, client_phone):
        self.client_phone = client_phone

    def set_appt_type(self, appt_type):
        self.appt_type = appt_type

    def schedule(self, client_name, client_phone, appt_type):
        self.client_name = client_name
        self.client_phone = client_phone
        self.appt_type = appt_type

    def cancel(self):
        self.client_name = ""
        self.client_phone = ""
        self.appt_type = 0

    def format_record(self):
        return f"{self.client_name},{self.client_phone},{self.appt_type},{self.day_of_week},{self.start_time_hour:02}"

    def __str__(self):
        return f"{self.client_name:>0s} {self.client_phone:>20} {self.day_of_week:>25s}{self.start_time_hour:>10}:00{'-':>2s} {self.get_end_time_hour()}:00{self.get_appt_type_desc():>20s}"

# Example usage:
appointment = Appointment(day_of_week="Saturday", start_time_hour=9)
appointment.set_client_name("Harvey")
appointment.set_client_phone("403-233-3944")
appointment.set_appt_type(1)

print(appointment.format_record())
print(str(appointment))
