<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: Tharun DP</h3>
<h3>Register Number: 212225240172


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>
<br>
<h3>Program:</h3>
```
import random

class HealthMonitoringAgent:
    def __init__(self, patient_data):
        self.patient_data = patient_data

    def monitor_health(self):
        # Print patient details
        print("===== Patient Details =====")
        print(f"Patient ID : {self.patient_data['patient_id']}")
        print(f"Name       : {self.patient_data['name']}")
        print(f"Age        : {self.patient_data['age']}")
        print("===========================\n")

        while True:
            current_health_state = self.sensors.get_health_state()

            # Display current health readings
            print("Current Health State:")
            print(f"Heart Rate    : {current_health_state['heart_rate']} bpm")
            print(f"Blood Pressure: {current_health_state['blood_pressure']} mmHg")
            print(f"Temperature   : {current_health_state['temperature']:.1f} °C")

            action = self.choose_action(current_health_state)
            self.actuators.perform_action(action)
            print()

            if action == "No specific action needed":
                break

    def choose_action(self, current_health_state):
        if current_health_state['heart_rate'] > 110:
            return "Alert healthcare provider: High heart rate detected"
        elif current_health_state['blood_pressure'] > 140:
            return "Alert healthcare provider: High blood pressure detected"
        elif current_health_state['temperature'] > 38:
            return "Recommend rest and monitor temperature"
        else:
            return "No specific action needed"


class HealthSensors:
    def get_health_state(self):
        return {
            'heart_rate': random.randint(60, 150),
            'blood_pressure': random.randint(90, 160),
            'temperature': random.uniform(36.0, 38.5)
        }


class HealthActuators:
    def perform_action(self, action):
        print("Action:", action)


if __name__ == "__main__":
    patient_data = {
        'patient_id': 1007,
        'name': 'THARUN ',
        'age': 18
    }

    health_sensors = HealthSensors()
    health_actuators = HealthActuators()

    health_monitoring_agent = HealthMonitoringAgent(patient_data)
    health_monitoring_agent.sensors = health_sensors
    health_monitoring_agent.actuators = health_actuators

    health_monitoring_agent.monitor_health()
```
