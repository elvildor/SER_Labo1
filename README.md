## SER Labo1
Jérémy Delay, Yoann Simonet
### Introduction
On souhaite enregistrer dans un document XML toutes 
les parties d’échecs ayant été jouées dans le cadre de la FSE dans différents tournois.

### DTD
    <!ELEMENT tournois (joueur+,tournoi+)>
    <!ELEMENT joueur (nom, prenom, classementELO)>
    <!ATTLIST joueur idFSE ID #REQUIRED>
    <!ELEMENT nom   (#PCDATA)>
    <!ELEMENT prenom(#PCDATA)>
    <!ELEMENT classementELO (#PCDATA)>
    <!ELEMENT tournoi (nomTournoi, partie+)>
    <!ATTLIST tournoi vainqueur IDREF #REQUIRED>
    <!ELEMENT nomTournoi (#PCDATA)>
    <!ELEMENT partie (joueurBlanc, joueurNoir, arbitre, date, deroulement)>
    <!ATTLIST partie score (1-0|0.5-0.5|0-1) #REQUIRED>
    <!ELEMENT joueurBlanc ANY>
    <!ATTLIST joueurBlanc idFES IDREF #REQUIRED>
    <!ELEMENT joueurNoir ANY>
    <!ATTLIST joueurNoir idFES IDREF #REQUIRED>
    <!ELEMENT arbitre (nom, prenom)>
    <!ELEMENT date (jour, mois, annee, heures, minutes)>
    <!ELEMENT jour  (#PCDATA)>
    <!ELEMENT mois  (#PCDATA)>
    <!ELEMENT annee (#PCDATA)>
    <!ELEMENT heures(#PCDATA)>
    <!ELEMENT minutes   (#PCDATA)>
    <!ELEMENT deroulement (tour)+>
    <!ELEMENT tour ((roque|deplacement), (echec|echecEtMat|matchNul)?)>
    <!ELEMENT roque EMPTY>
    <!ATTLIST roque type (PetitRoque|GrandRoque) #REQUIRED>
    <!ELEMENT deplacement (caseDepart?, caseArrivee, pieceMangee?, promotionPion?)>
    <!ATTLIST deplacement piece (Tour|Cavalier|Fou|Dame|Roi|Pion) #REQUIRED>
    <!ELEMENT caseDepart (#PCDATA)>
    <!ELEMENT caseArrivee (#PCDATA)>
    <!ELEMENT pieceMangee EMPTY>
    <!ATTLIST pieceMangee type (Tour|Cavalier|Fou|Dame|Pion) #REQUIRED >
    <!ELEMENT promotionPion EMPTY>
    <!ATTLIST promotionPion type (Tour|Cavalier|Fou|Dame) #REQUIRED >
    <!ELEMENT echec EMPTY>
    <!ELEMENT echecEtMat EMPTY>
    <!ELEMENT matchNul EMPTY>

### XML


    <?xml version="1.0" encoding="UTF-8"?>
	<tournois>
		<joueur idFSE = "P1">
			<nom>simonet</nom>
			<prenom>toto</prenom>
			<classementELO>2500</classementELO>
		</joueur>
		<joueur idFSE = "P2">
			<nom>simonet</nom>
			<prenom>titi</prenom>
			<classementELO>2500</classementELO>
		</joueur>
		<joueur idFSE = "P3">
			<nom>simonet</nom>
			<prenom>tata</prenom>
			<classementELO>2500</classementELO>
		</joueur>
		<joueur idFSE = "P4">
			<nom>delay</nom>
			<prenom>tutu</prenom>
			<classementELO>2500</classementELO>
		</joueur>
		<joueur idFSE = "P5">
			<nom>delay</nom>
			<prenom>moi</prenom>
			<classementELO>2500</classementELO>
		</joueur>
		<joueur idFSE = "P6">
			<nom>delay</nom>
			<prenom>lui</prenom>
			<classementELO>2500</classementELO>
		</joueur>
		<tournoi vainqueur = "P1">
			<nomTournoi>tournoi du lac</nomTournoi>
			<partie score = "1-0">
				<joueurBlanc idFES = "P1"/>
				<joueurNoir idFES = "P2"/>
				<arbitre>
					<nom>tata</nom>
					<prenom>jone</prenom>
				</arbitre>
				<date>
					<jour>21</jour >
					<mois>11</mois >
					<annee >2019</annee >
					<heures>17</heures >
					<minutes>32</minutes>
				</date>
				<deroulement>
					<tour>
						<roque type = "PetitRoque"/>
						<echec/>
					</tour>
					<tour>
						<deplacement piece = "Fou">
							<caseDepart>C1</caseDepart>
							<caseArrivee>B2</caseArrivee >
							<pieceMangee type = "Dame"/>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Pion">
							<caseDepart>A7</caseDepart>
							<caseArrivee>A8</caseArrivee >
							<promotionPion type = "Dame"/>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Roi">
							<caseArrivee>C4</caseArrivee >
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Dame">
							<caseDepart>A4</caseDepart>
							<caseArrivee>C4</caseArrivee >
						</deplacement>
						<echecEtMat/>
					</tour>
				</deroulement>
			</partie>
			<partie score = "0.5-0.5">
				<joueurBlanc idFES = "P1"/>
				<joueurNoir idFES = "P2"/>
				<arbitre>
					<nom>tata</nom>
					<prenom>jone</prenom>
				</arbitre>
				<date>
					<jour>30</jour>
					<mois>11</mois>
					<annee >2019</annee>
					<heures>17</heures>
					<minutes>32</minutes>
				</date>
				<deroulement>
					<tour>
						<roque type = "GrandRoque"/>
					</tour>
					<tour>
						<deplacement piece = "Fou">
							<caseArrivee>B2</caseArrivee>
							<pieceMangee type = "Fou"/>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Pion">
							<caseDepart>A7</caseDepart>
							<caseArrivee>A8</caseArrivee>
							<promotionPion type = "Dame"/>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Roi">
							<caseArrivee>C4</caseArrivee>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Dame">
							<caseDepart>A4</caseDepart>
							<caseArrivee>C4</caseArrivee>
						</deplacement>
						<matchNul/>
					</tour>
				</deroulement>
			</partie>
		</tournoi>
		<tournoi vainqueur = "P6">
			<nomTournoi >tous les coups sont permis</nomTournoi>
			<partie score = "1-0" >
				<joueurBlanc idFES = "P5"/>
				<joueurNoir idFES = "P2"/>
				<arbitre>
					<nom>tata</nom>
					<prenom>jone</prenom>
				</arbitre>
				<date>
					<jour>21</jour >
					<mois>11</mois >
					<annee >2019</annee >
					<heures>17</heures >
					<minutes>32</minutes>
				</date>
				<deroulement>
					<tour>
						<roque type = "PetitRoque"/>
						<echec/>
					</tour>
					<tour>
						<deplacement piece = "Fou">
							<caseDepart>C1</caseDepart>
							<caseArrivee>B2</caseArrivee >
							<pieceMangee type = "Dame"/>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Pion">
							<caseDepart>A7</caseDepart>
							<caseArrivee>A8</caseArrivee >
							<promotionPion type = "Dame"/>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Roi">
							<caseArrivee>C4</caseArrivee >
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Dame">
							<caseDepart>A4</caseDepart>
							<caseArrivee>C4</caseArrivee >
						</deplacement>
						<echecEtMat/>
					</tour>
				</deroulement>
			</partie>
			<partie score = "1-0">
				<joueurBlanc idFES = "P6"/>
				<joueurNoir idFES = "P2"/>
				<arbitre>
					<nom>tata</nom>
					<prenom>yoyo</prenom>
				</arbitre>
				<date>
					<jour>30</jour>
					<mois>11</mois>
					<annee >2056</annee>
					<heures>23</heures>
					<minutes>59</minutes>
				</date>
				<deroulement>
					<tour>
						<roque type = "GrandRoque"/>
					</tour>
					<tour>
						<deplacement piece = "Fou">
							<caseArrivee>B2</caseArrivee>
							<pieceMangee type = "Fou"/>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Pion">
							<caseDepart>A7</caseDepart>
							<caseArrivee>A8</caseArrivee>
							<promotionPion type = "Dame"/>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Roi">
							<caseArrivee>C4</caseArrivee>
						</deplacement>
					</tour>
					<tour>
						<deplacement piece = "Dame">
							<caseDepart>A4</caseDepart>
							<caseArrivee>C4</caseArrivee>
						</deplacement>
						<echecEtMat/>
					</tour>
				</deroulement>
			</partie>
		</tournoi>
	</tournois>





### Une capture d’écran

Code validé sur https://www.online-toolz.com/tools/xml-validator.php
![](../Capture.PNG)
![Capture](https://user-images.githubusercontent.com/47739482/54495522-df715280-48e4-11e9-8ffc-167dab79655e.PNG)

### Réponses aux différentes questions posées

#### Imaginons que vous souhaitez enregistrer le classement ELO que chaque joueur d’une partie avait au moment où elle a été jouée, qu’est-ce qu’il faudrait modifier dans votre DTD?
On pourrait ajouter un attribut ELOjoueur dans chaque partie.

    <!ELEMENT joueurBlanc ANY>
    <!ATTLIST joueurBlanc idFES IDREF #REQUIRED>
    <!ATTLIST joueurBlanc ELO #REQUIRED>
    <!ELEMENT joueurNoir ANY>
    <!ATTLIST joueurNoir idFES IDREF #REQUIRED>
    <!ATTLIST joueurBlanc ELO #REQUIRED>
 


#### Est-ce possible dans votre DTD de représenter le fait qu’il ne peut y avoir que 20 parties au maximum dans un tournoi? Si oui,comment?
oui

exemple:
`<!ELEMENT tournoi (nomTournoi, partie?, partie?, ......, partie?)> <!-- avec 20x "partie" -->` 

Remarque : Ce serait très lourd.
#### Est-ce possible dans votre DTD de représenter le fait que les 2 joueurs d’une partie doivent être différents?
oui

exemple:

    <!ELEMENT partie (joueurBlanc, joueurNoir, arbitre, date, deroulement)>
    <!ELEMENT joueurBlanc (nom, prenom, classementELO)>
    <!ATTLIST joueurBlanc idFSE ID #REQUIRED>
    <!ELEMENT classementELO (#PCDATA)>
    <!ELEMENT joueurNoir (nom, prenom, classementELO)>
    <!ATTLIST joueurNoir idFSE ID #REQUIRED>

Mais cette implémantation n'est pas pratique car un joueur va très probablement vouloir jouer plus qu'une partie.

### Conclusion
Ce laboratoire était intéressant car on a pu construire notre propre fichier XML selon un cahier des charges fourni. On a pu y réfléchir et essayer de deviner quels étaient les éléments important à mettre en balise ou en attribut et quels élément étaient liés entre eux (déplacement/roque, par exemple).  

Il nous a aussi permis de voir les possibilités (DTD, structure en arbre) et les limitations du XML.

Le point faible de ce labo était la première session où l'on n'avait encore rien vu et l'on était laché dans vide. On a dû aller lire la suite du cours (en auto-didacte) pour savoir quoi faire afin de ne pas perdre une session de labo.




