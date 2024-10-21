# react-state-checkpoint

Création d'une application React avec un composant de classe et gestion d'état
1. Création du projet avec Create React App
Bash
npx create-react-app mon-projet-react
cd mon-projet-react
Use code with caution.

2. Modification de App.js en composant de classe
JavaScript
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      personne:   
 {
        fullName: 'John Doe',
        bio: 'Je suis un développeur',
        imgSrc: 'path/to/your/image.jpg',
        profession: 'Développeur web'
      },
      montre: false,
      intervalle: 0
    };
  }

  componentDidMount() {
    this.intervalId = setInterval(() => {
      this.setState({ intervalle: this.state.intervalle + 1 });
    }, 1000);
  }

  componentWillUnmount() {
    clearInterval(this.intervalId);
  }

  toggleShow = () => {
    this.setState({ montre: !this.state.montre });
  }

  render() {
    const { fullName, bio, imgSrc, profession } = this.state.personne;
    const { montre, intervalle } = this.state;

    return (
      <div>
        <button onClick={this.toggleShow}>Afficher/Masquer</button>
        {montre && (
          <div>
            <h2>{fullName}</h2>
            <img src={imgSrc} alt={fullName} />
            <p>{bio}</p>
            <p>Profession: {profession}</p>
            <p>Temps écoulé : {intervalle} secondes</p>
          </div>
        )}
      </div>
    );
  }
}

export default App;
Use code with caution.

Explications :
État initial: L'état initial du composant contient les informations sur la personne, un booléen pour contrôler l'affichage et un compteur d'intervalle.
componentDidMount: Cette méthode est appelée après le premier rendu. Elle initialise un intervalle qui incrémente le compteur toutes les secondes.
componentWillUnmount: Cette méthode est appelée juste avant que le composant soit démonté. Elle permet de nettoyer l'intervalle pour éviter les fuites de mémoire.
toggleShow: Cette méthode inverse la valeur de montre à chaque clic sur le bouton.
render: Le rendu conditionnel affiche le profil de la personne uniquement si montre est vrai. L'intervalle est affiché en dessous du profil.
Fonctionnement :
Le composant est monté et l'intervalle est démarré.
Le bouton affiche ou masque le profil de la personne en fonction de l'état montre.
Le compteur d'intervalle s'incrémente toutes les secondes et s'affiche à l'écran.
Points clés :
État: L'état est utilisé pour stocker les données qui peuvent changer au cours du temps.
Cycle de vie: Les méthodes componentDidMount et componentWillUnmount sont utilisées pour gérer les effets secondaires liés au cycle de vie du composant.
Rendu conditionnel: Le rendu conditionnel permet d'afficher ou de masquer des éléments en fonction de l'état.
Interval: setInterval est utilisé pour exécuter une fonction à intervalles réguliers.
Améliorations possibles:

Formatage de l'intervalle: Vous pouvez utiliser une bibliothèque comme moment.js pour formater l'affichage de l'intervalle.
Optimisations: Pour des applications plus complexes, vous pouvez utiliser des techniques d'optimisation comme React.memo ou useMemo pour éviter les rendus inutiles.
Styles: Vous pouvez ajouter des styles CSS pour améliorer l'apparence de votre composant.
Ce code fournit une base solide pour créer des composants React plus complexes avec gestion d'état et interactions utilisateur.
