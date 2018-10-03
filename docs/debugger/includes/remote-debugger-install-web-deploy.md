---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244117"
---
1. Se si prevede di distribuire le applicazioni con distribuzione Web in Visual Studio, installare la versione più recente di distribuzione Web nel server.

    Per installare distribuzione Web, usare il [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Per trovare il collegamento di installazione guidata piattaforma Web da IIS, selezionare **IIS** nel riquadro sinistro di Server Manager. Fare doppio clic su server e selezionare **Internet Information Services (IIS) Manager**.)

    L'installazione guidata piattaforma Web, si trova distribuzione Web nella scheda applicazioni. È anche possibile ottenere direttamente da un programma di installazione di [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Verificare che distribuzione Web è in esecuzione correttamente aprendo **Pannello di controllo > sistema e sicurezza > Strumenti di amministrazione > servizi** e assicurarsi che **servizio agente distribuzione Web** è in esecuzione (la nome del servizio è diverso nelle versioni precedenti).

    Se il servizio dell'agente non è in esecuzione, avviarlo. Se non è presente in tutti, andare al **Pannello di controllo > programmi > Disinstalla un programma**, trovare **Microsoft Web Deploy <version>** . Scegliere di **Change** l'installazione e assicurarsi che si sceglie **verrà installato nell'unità disco rigido locale** per i componenti di distribuzione Web. Completare i passaggi di installazione di modifica.