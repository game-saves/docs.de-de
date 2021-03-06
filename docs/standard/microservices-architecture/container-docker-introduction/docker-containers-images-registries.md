---
title: Docker-Container, -Images und -Registrierungen
description: .NET-Microservicesarchitektur für .NET-Containeranwendungen | Docker-Container, -Images und -Registrierungen
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: f10d7d03bbf88ed8f7a89a5d3919a39b3c124ae0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130233"
---
# <a name="docker-containers-images-and-registries"></a>Docker-Container, -Images und -Registrierungen

Mithilfe von Docker erstellen Entwickler Apps und Dienste und packen diese und ihre Abhängigkeiten in ein Containerimage. Ein Image entspricht einer statischen Darstellung der Apps oder Dienste und von deren Konfigurationen und Abhängigkeiten.

Für die Ausführung einer App oder eines Diensts wird das Image der App oder des Diensts instanziiert, um einen Container zu erstellen, der auf dem Docker-Host ausgeführt wird. Container werden zunächst in einer Entwicklungsumgebung oder auf einem PC getestet.

Entwickler sollten Images in einer Registrierung speichern. Diese fungiert als Bibliothek für Images und ist bei der Bereitstellung für Produktionsorchestratoren erforderlich. Docker verwaltet eine öffentliche Registrierung über den [Docker-Hub](https://hub.docker.com/). Andere Anbieter stellen Registrierungen für verschiedene Imagesammlungen bereit, einschließlich der [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternativ können Unternehmen eine private lokale Registrierung für eigene Docker-Images einrichten.

In Abbildung 2-4 wird dargestellt, wie Images und Registrierungen in Docker mit anderen Komponenten in Beziehung stehen. Die Angebote verschiedener Anbieter für Registrierungen werden ebenfalls dargestellt.

![Grundlegende Taxonomie in Docker: Die Registrierung funktioniert wie ein Bücherregal, in dem Images gespeichert und für den Abruf zum Erstellen von Containern verfügbar sind, in denen Dienste oder Web-Apps ausgeführt werden. Private Docker-Registrierungen gibt es lokal und in der öffentlichen Cloud. Docker Hub ist eine öffentliche Registrierung, die von Docker betrieben wird, die Docker Trusted Registry ist eine für Unternehmen geeignete Lösung, und Azure bietet die Azure Container Registry an. AWS, Google und andere verfügen ebenfalls über Containerregistrierungen.](./media/image5.PNG)

**Abbildung 2-4**. Taxonomie der Docker-Begriffe und -Konzepte

Durch das Einfügen von Images in eine Registrierung können Sie statische und unveränderliche Komponenten der Anwendung speichern, einschließlich aller Abhängigkeiten auf Frameworkebene. Diese Images können dann mit einer Versionsangabe versehen und in mehreren Umgebungen bereitgestellt werden. Dadurch wird eine konsistente Bereitstellungseinheit bereitgestellt.

Private Imageregistrierungen, die lokal oder in der Cloud gehostet werden, werden empfohlen, wenn:

-   Ihre Images wegen Vertraulichkeit nicht öffentlich freigegeben werden dürfen

-   Sie eine minimale Netzwerklatenz zwischen Ihren Images und der ausgewählten Bereitstellungsumgebung erzielen möchten Wenn Ihre Produktionsumgebung beispielsweise die Azure-Cloud ist, möchten Sie Ihre Images wahrscheinlich in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) speichern, um eine minimale Netzwerklatenz zu erzielen. Ähnliches gilt, wenn Ihre Produktionsumgebung lokal ist: Dann Sie möchten vermutlich sicherstellen, dass ein lokaler Docker Trusted Registry-Dienst innerhalb desselben lokalen Netzwerks verfügbar ist.

>[!div class="step-by-step"]
>[Zurück](docker-terminology.md)
>[Weiter](../net-core-net-framework-containers/index.md)