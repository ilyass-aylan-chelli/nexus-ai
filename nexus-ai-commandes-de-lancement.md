# ⚡ NEXUS AI — Toutes les commandes de lancement

Fiche pratique : chaque commande, dans l'ordre, pour passer de l'installation au lancement de NEXUS AI.

---

## 1️⃣ Ollama — le moteur de modèles locaux

### Démarrer Ollama en arrière-plan (obligatoire avant chaque session)

```cmd
ollama serve
```

⚠️ Cette commande **occupe la fenêtre CMD**. Laisse-la ouverte et ouvre une **nouvelle fenêtre CMD** pour la suite.
> Si `ollama serve` affiche une erreur "port already in use", c'est qu'Ollama tourne déjà — parfait, rien à faire.

### Télécharger le modèle (une seule fois)

```cmd
ollama pull qwen2.5:7b
```

### Tester le modèle en mode chat

```cmd
ollama run qwen2.5:7b
```

Puis pose une question. Taper `/bye` pour quitter.

### Vérifier qu'Ollama répond bien sur son API locale

```cmd
curl http://localhost:11434
```

Réponse attendue : `Ollama is running`

---

## 2️⃣ Le projet NEXUS AI

### Entrer dans le projet et activer l'environnement Python

```cmd
cd C:\NEXUS-AI
.venv\Scripts\activate
```

> `(NEXUS-AI)` doit apparaître au début de la ligne. Sinon, l'activation a échoué.

### Lancer le système multi-agents

```cmd
python main.py
```

Puis saisir l'objectif quand le prompt `🎯 Objectif pour NEXUS AI :` apparaît.
Le rapport final est sauvegardé dans `reports\rapport_final.md`.

---

## 3️⃣ Séquence complète typique (deux fenêtres CMD)

| Fenêtre | Commandes | Rôle |
|---|---|---|
| **CMD 1** | `ollama serve` | Laisse tourner — c'est le serveur de modèles |
| **CMD 2** | `cd C:\NEXUS-AI` puis `.venv\Scripts\activate` puis `python main.py` | Le système multi-agents |

---

## 4️⃣ Commandes utiles au quotidien

| Commande | Usage |
|---|---|
| `ollama list` | Lister les modèles installés |
| `ollama rm qwen2.5:3b` | Supprimer un modèle |
| `ollama ps` | Voir le modèle chargé en mémoire |
| `python -c "import crewai; print('OK')"` | Vérifier que CrewAI est bien installé |
| `deactivate` | Désactiver l'environnement virtuel |

---

## 5️⃣ Si ça ne marche pas

| Symptôme | Correction |
|---|---|
| `Connection error` au lancement | CMD 1 absent : lancer `ollama serve` |
| `(NEXUS-AI)` n'apparaît pas | Relancer `.venv\Scripts\activate` dans `C:\NEXUS-AI` |
| `python n'est pas reconnu` | Réinstaller Python avec **Add Python to PATH** coché |
| Tout est très lent | Fermer les applis lourdes, ou passer à `qwen2.5:3b` dans `main.py` |