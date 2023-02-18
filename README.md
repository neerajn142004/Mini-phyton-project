# Mini-phyton-project
Artificial Intelligence
mport time

class CountdownTimer:
    def _init_(self, minutes):
        self.minutes = minutes
        self.seconds = minutes * 60
        self.is_running = False
        self.is_paused = False
        self.start_time = 0
        self.pause_time = 0

    def start(self):
        self.is_running = True
        self.start_time = time.time()
        while self.seconds > 0 and self.is_running:
            if not self.is_paused:
                minutes, seconds = divmod(self.seconds, 60)
                print(f"{minutes:02d}:{seconds:02d}")
                time.sleep(1)
                self.seconds -= 1
            else:
                self.pause_time = time.time()
                time.sleep(1)

    def stop(self):
        self.is_running = False
        self.is_paused = False
        self.start_time = 0
        self.pause_time = 0
        self.seconds = self.minutes * 60

    def pause(self):
        self.is_paused = True

    def resume(self):
        self.is_paused = False
        self.start_time += time.time() - self.pause_time

if _name_ == '_main_':
    timer = CountdownTimer(25)  # 25 minutes timer
    timer.start()
