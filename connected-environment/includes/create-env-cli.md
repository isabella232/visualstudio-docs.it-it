---
ms.topic: include
ms.openlocfilehash: 97f9885780c9f697cfc6a58b78054761fdcd725d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
## <a name="create-a-kubernetes-development-environment-in-azure"></a>Creare un ambiente di sviluppo Kubernetes in Azure
Con Connected Environment è possibile creare ambienti basati su Kubernetes gestiti completamente da Azure e ottimizzati per lo sviluppo. Il comando crea un ambiente denominato `mydevenvironment` in `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Posizioni supportate: `eastus`, `westeurope`

> [!Note]
> Per l'esecuzione di questo comando sono necessari circa 6 minuti. È possibile continuare con la lettura di questa guida senza aspettare.
