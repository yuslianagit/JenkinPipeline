import psutil
import requests

class SystemMonitor:
    @staticmethod
    def check_disk_usage():
        disk_usage_percent = psutil.disk_usage('/').percent
        return disk_usage_percent > 20

    @staticmethod
    def check_cpu_utilization():
        cpu_utilization_percent = psutil.cpu_percent()
        return cpu_utilization_percent < 75

    @staticmethod
    def check_localhost_availability():
        try:
            localhost_availability = requests.get('http://localhost')
            return localhost_availability.status_code == 200
        except requests.ConnectionError:
            return False

    @staticmethod
    def check_internet_availability():
        try:
            internet_availability = requests.get('http://www.google.com')
            return internet_availability.status_code == 200
        except requests.ConnectionError:
            return False

def main():
    monitor = SystemMonitor()

    disk_check = monitor.check_disk_usage()
    cpu_check = monitor.check_cpu_utilization()
    localhost_check = monitor.check_localhost_availability()
    internet_check = monitor.check_internet_availability()

    if not (disk_check and cpu_check):
        print("ERROR! Disk usage or CPU usage failed.")
    elif localhost_check and internet_check:
        print("Everything is OK.")
    else:
        print("Network checks failed.")

if __name__ == "__main__":
    main()
