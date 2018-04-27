---
ms.topic: include
ms.openlocfilehash: 94e82185b05900101f91e4b368bb30d2aaceac03
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
## <a name="clean-up"></a>Eseguire la pulizia
Per eliminare completamente un ambiente Connected Environment in Azure, inclusi tutti i servizi in esecuzione al suo interno, usare il comando `vsce env rm`. Tenere presente che questa azione è irreversibile.

L'esempio seguente elenca gli ambienti Connected Environment nella sottoscrizione di Azure attiva, e quindi elimina l'ambiente denominato 'myenv' incluso nel gruppo di risorse 'myenv-rg'.

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

