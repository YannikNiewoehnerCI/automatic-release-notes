# Release & Versioning Guide

Dieses Repository verwendet einen **PR-basierten Release-Prozess** mit automatisierten
Release Notes (Keep a Changelog) und Deployments über **GitHub Actions**.

Ziel:
- reproduzierbare Deployments
- klare Trennung zwischen Entwicklung, Staging und Produktion
- nachvollziehbare Änderungen über Release Notes / Tags

---

## Branch-Modell

| Branch | Zweck |
|--------|--------|
| `dev`  | Feature- & Entwicklungsbranch |
| `stage` | Staging (Pre-Production Deployment) |
| `main` | Produktion (Production Deployment) |

Änderungen werden **immer per Pull Request** gemerged.

---

## PR-Labels (Pflicht)

Jeder Pull Request **muss** mindestens eines der folgenden Labels haben:

| Label | Bedeutung | Changelog-Sektion |
|--------|------------|-------------------|
| `feature` | Neues Feature | Added |
| `bug` | Bugfix | Fixed |
| `documentation` | Doku-Änderung | Documentation |
| `security` | Security-relevant | Security |
| `removed` | Entfernte Funktion | Removed |
| `skip-changelog` | Ignorieren | – |

Diese Labels sind die **Single Source of Truth** für Release Notes.

---

## Versionierung (SemVer)

Wir folgen **Semantic Versioning**:

**MAJOR.MINOR.PATCH**

Beispiele:
- `1.2.0` → neues Feature (minor)
- `1.2.1` → Bugfix (patch)
- `2.0.0` → Breaking Change (major)

Hinweis: In einer Webapp dienen Versionen primär der **Nachvollziehbarkeit**
(Monitoring, Rollbacks, Incident-Analyse), nicht der Distribution von Artefakten an Dritte.

---

## Releases (optional)

Ein Release/Tag kann erstellt werden, wenn `stage → main` gemerged wird.

### Format
- `vX.Y.Z`

Beispiel:
- `v1.2.2`

### Regeln
- Ein Release wird **nur einmal erstellt**
- Existiert ein Release bereits → Workflow überspringt ihn
- Stable Releases haben **kein Pre-Release-Suffix**