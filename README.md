# SoSe_SWE_Ergometer
# my_functions.py
def estimate_max_hr(age_years : int , sex : str) -> int:
  """
  See https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4124545/ for different formulas
  """
  if sex == "male":
    max_hr_bpm =  223 - 0.9 * age_years
  elif sex == "female":
    max_hr_bpm = 226 - 1.0 *  age_years
  else:
    # der input() öffnet ein Eingabefenster für den Nutzer und speichert die Eingabe
    max_hr_bpm  = input("Enter maximum heart rate:")
  return int(max_hr_bpm)

def build_person(first_name, last_name, sex, age) -> dict:
    """Returns a dictionary of information about a supervisor or subject."""
    person_dict = { "first_name" : first_name,
             "last_name" : last_name,
             "age" : age,
             "estimate_max_hr" : estimate_max_hr(age,sex)}
    return person_dict

def build_experiment(experiment_name, date, supervisor, subject) -> dict:
    """Returns a dictionary of information about an experiment."""
    experiment_dict = {"experiment_name" : experiment_name,
            "date" : date,
            "supervisor" :   supervisor,
            "subject" :   subject
            }
    return experiment_dict

# main.py
from my_functions import build_person, build_experiment

if __name__ == "__main__":
    # Supervisor-Daten
    supervisor = build_person("Jakob", "Haas", "male", 19)

    # Versuchsperson-Daten
    subject = build_person("Hanne", "Müller", "female", 56)

    # Experiment-Daten
    experiment = build_experiment("Herzfrequenz-Analyse", "2025-03-24", supervisor, subject)

    # Ausgabe des Experiment-Dictionarys
    print(experiment)
