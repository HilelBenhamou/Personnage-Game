# Personnage-Game
Inventaire des Personnages

class Personnage {
  constructor (nom, sante , force, xp, or, clef){
    this.nom=nom;
    this.sante=sante;
    this.force=force;
    this.xp=0;
    this.or=10;
    this.clef=1;}
    decrire(){
      return `${this.nom} a ${this.sante} points de sante, ${this.force} en force et ${this.xp} points d'experience, ${this.or} pieces d'or et ${this.clef} clé`;
    }
    attaquer(cible){
      if (this.sante>0){
        const degats =this.force;
        console.log(`${this.nom} attaque ${cible.nom} et lui inflige ${degats} points de degats`);
        cible.sante-=degats;
        if (cible.sante>0)
          {
            console.log(`${cible.nom} a encore ${cible.sante} points de sante, ${cible.force} de force, ${cible.or} pieces d'or, ${cible.clef} clés`);
          }
        else{
          cible.sante=0;
          const bonusXp=10;
          this.xp+=bonusXp;
          this.or+=cible.or;
          this.clef+=cible.clef;
          
          cible.or=0;
          cible.clef=0;
          
          
          console.log(`${cible.nom} est mort et ${this.nom} a ${this.xp} points d'experience en plus, ainsi que ${this.or} pieces d'or, et ${this.clef} clés`);
        }
      }
      else{
        console.log(`${this.nom} n'a plus de points de vie et ne peux plus attaquer`);
      }
    } 
}



// "Aurora a 150 points de vie, 25 en force et 0 points d'expérience, 10 pièces d'or et 1 clé(s)"
const aurora = new Personnage("Aurora", 150, 25);

console.log(aurora.decrire());

const monstre = new Personnage("ZogZog", 20, 10);
console.log (monstre.decrire());
monstre.attaquer(aurora);
aurora.attaquer(monstre); // Le monstre est tué

// "Aurora a 140 points de vie, 25 en force et 10 points d'expérience, 20 pièces d'or et 2 clé(s)"
console.log(aurora.decrire());

