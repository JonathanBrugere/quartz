# Excel VBA Learning

1 : Déclare les variables
2 : Ecrire les conditions avec :
If then Else end if  :  If range("A1")  = 15 Then  range("A2") = 2 sinon range("A2") = 3
While wend : tant qu'on respect la condition : While cells(1,Ligne) <>"" ......action à réaliser puis Wend  :  Tant que la condition est remplie… Faire »
Do/ If / Loop while :Faire ...  Tant que la condition est remplie »
For/ exit for/Next

![[Mes documents/_resources/Excel_VBA_Learning.resources/image.png]]![[Mes documents/_resources/Excel_VBA_Learning.resources/image.1.png]]

==Public Sub== Comptage==()==

==Dim== bonbon ==As Long==
==Dim== Ligne ==As Long==
Ligne = 1 ' Ligne est initialisé à 1

==While== Feuil1.Cells(Ligne, 1) <> "" ' Tant que la ligne est vide
bonbon = bonbon + 1 ' rajouter 1 au compteur
Ligne = Ligne + 1 ' descendre d'une ligne'
==Wend==

==Dim== reponse ==As Long==
reponse = ==MsgBox==("j'ai dans ma poche " & bonbon & " bonbons" \_
& Chr(10) & Chr(13) & \_
" Sauf erreur de ma part", vbYesNo + vbQuestion, "Compteur")

==If== reponse = vbYes ==Then==
==MsgBox== "super"
==Else==
==MsgBox== " Mince, une ou plusieurs cellule doient être vide"
==End If==

==End Sub==
#langageprogramation