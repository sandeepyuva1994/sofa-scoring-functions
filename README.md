# sofa-scoring-functions
q sofa and sofa scoring
def sofa(file):
    import pandas as pd
    data=pd.read_table(file,sep="|")
result_qsofa = []
for a,b in zip(data["HR"], data["SBP"]): 
    if a>=22 and b<=100: 
        result_qsofa.append(1)
    else:
        result_qsofa.append(0)
data["qSOFA"]=result_qsofa

#sofa scoring
#Platelets < 100
#bilurubin_total >= 2
#Creatinine >= 2
result_sofa= []
for a,b,c in zip(data["Platelets"], data["Bilirubin_total"],data["Creatinine"]): 
    if a>100 and b>=2 and c>=2: 
        result_sofa.append(1)
    else:
        result_sofa.append(0)
data["SOFA"]=result_sofa
#this data frame should be written into a folder with
