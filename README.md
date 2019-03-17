## SER Labo1
### Introduction
On souhaite enregistrer dans un document XML toutes 
les parties d’échecs ayant été jouées dans le cadre de la FSE dans différents tournois.
### DTD
    <?xml version="1.0" encoding="UTF-8"?>
    <!ELEMENT tournois (tournoi)+>
    <!ELEMENT tournoi (nomTournoi, partie+)>
    <!ATTLIST tournoi vainqueur IDREF #REQUIRED>
    <!ELEMENT nomTournoi (#PCDATA)>
    <!ELEMENT partie (joueur*,joueurBlanc, joueurNoir, arbitre, date, deroulement)>
    <!ATTLIST partie score (1-0|0.5-0.5|0-1) #REQUIRED>
    <!ELEMENT joueur (nom, prenom, classementELO)>
    <!ATTLIST joueur idFSE ID #REQUIRED>
    <!ELEMENT nom   (#PCDATA)>
    <!ELEMENT prenom(#PCDATA)>
    <!ELEMENT classementELO (#PCDATA)>
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
    	<tournoi vainqueur = "P1">
    		<nomTournoi>tournoi du lac</nomTournoi>
    		<partie score = "1-0">
    			<joueur idFSE = "P1">
    				<nom>toto</nom>
    				<prenom>simonet</prenom>
    				<classementELO>2500</classementELO>
    			</joueur>
    			<joueur idFSE = "P2">
    				<nom>titi</nom>
    				<prenom>simonet</prenom>
    				<classementELO>2500</classementELO>
    			</joueur>
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
    			<joueur idFSE = "P3">
    				<nom>toto</nom>
    				<prenom>simonet</prenom>
    				<classementELO>2500</classementELO>
    			</joueur>
    			<joueur idFSE = "P4">
    				<nom>titi</nom>
    				<prenom>simonet</prenom>
    				<classementELO>2500</classementELO>
    			</joueur>
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
    					<echecEtMat/>
    				</tour>
    			</deroulement>
    		</partie>
    	</tournoi>
    	<tournoi vainqueur = "P1">
    		<nomTournoi >tous les coups sont permis</nomTournoi>
    		<partie score = "1-0" >
    			<joueur idFSE = "P5">
    				<nom>titi</nom>
    				<prenom>simonet</prenom>
    				<classementELO>2500</classementELO>
    			</joueur>
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
    			<joueur idFSE = "P6">
    				<nom>toto</nom>
    				<prenom>simonet</prenom>
    				<classementELO>2500</classementELO>
    			</joueur>
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


###une capture d’écran



code valider sur https://www.online-toolz.com/tools/xml-validator.php
![Capture](https://user-images.githubusercontent.com/47739482/54474526-262c5300-47e6-11e9-9d08-32f6601f3292.PNG)
### Réponses aux différentes questions posées


####Imaginons que vous souhaitez enregistrer le classement ELO que chaque joueur d’une partie avait au moment où elle a été jouée, qu’est-ce qu’il faudrait modifier dans votre DTD?
On pourrais ajouter un element ELOjoueur dans chaque partie.

    <!ELEMENT joueurBlanc ANY>
    <!ATTLIST joueurBlanc idFES IDREF #REQUIRED>
    <!ATTLIST joueurBlanc ELO #REQUIRED>
    <!ELEMENT joueurNoir ANY>
    <!ATTLIST joueurNoir idFES IDREF #REQUIRED>
    <!ATTLIST joueurBlanc ELO #REQUIRED>

=======
#### Imaginons que vous souhaitez enregistrer le classement ELO que chaque joueur d’une partie avait au moment où elle a été jouée, qu’est-ce qu’il faudrait modifier dans votre DTD?
Rien
>>>>>>> f53aa3626e639d0b09e266e55bce3a3e037ea013

#### Est-ce possible dans votre DTD de représenter le fait qu’il ne peut y avoir que 20 parties au maximum dans un tournoi? Si oui,comment?
oui

exemple:
`<!ELEMENT tournoi (nomTournoi, partie1?,partie2?, ......,partie20?)>` 

remarque : Ce serais très lourd.
#### Est-ce possible dans votre DTD de représenter le fait que les 2 joueurs d’une partie doivent être différents?
oui

exemple:

    <!ELEMENT partie (joueurBlanc, joueurNoir, arbitre, date, deroulement)>
    <!ELEMENT joueurBlanc (nom, prenom, classementELO)>
    <!ATTLIST joueurBlanc idFSE ID #REQUIRED>
    <!ELEMENT classementELO (#PCDATA)>
    <!ELEMENT joueurNoir (nom, prenom, classementELO)>
    <!ATTLIST joueurNoir idFSE ID #REQUIRED>


Mais cette implémantation n' est pas pratique car un joueur va très probablement vouloir jouer d' autre parties.

###Conclusion







