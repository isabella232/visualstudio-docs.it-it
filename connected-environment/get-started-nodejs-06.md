---
title: 'Creare un ambiente di sviluppo Node.js con i contenitori usando Kubernetes nel cloud con Visual Studio - Passaggio 6: Informazioni sullo sviluppo in team | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: douge
ms.openlocfilehash: 6a17dfc3eeebccf1508ea3f69aecb53d067de7af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31883579"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introduzione a Connected Environment con Node.js

Passaggio precedente: [Chiamare un servizio in esecuzione in un contenitore separato](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Eccolo in azione:
1. Passare alla finestra di Visual Studio Code per `mywebapi` e apportare una modifica al codice per il gestore predefinito `/` GET, ad esempio:

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [avanti](get-started-nodejs-07.md)

