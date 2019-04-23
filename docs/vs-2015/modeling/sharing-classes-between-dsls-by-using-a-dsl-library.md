---
title: Condivisione di classi tra DSL usando una libreria DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1f5b12dce533aa03cf12efd8a6f9fc26ce990e5d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073826"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Condivisione di classi tra DSL utilizzando una libreria DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK, è possibile creare una definizione DSL incompleta che è possibile importare in un altro linguaggio specifico di dominio. Ciò consente di scomporre le parti comuni dei modelli simili.  
  
## <a name="creating-and-using-dsl-libraries"></a>Creare e utilizzare le librerie DSL  
  
#### <a name="to-create-a-dsl-library"></a>Per creare una libreria DSL  
  
1. Creare un nuovo progetto DSL e scegliere il modello di soluzione della libreria DSL.  
  
     Verrà creato un singolo progetto DSL con un modello vuoto.  
  
2. È possibile aggiungere classi di dominio, relazioni, forme e così via.  
  
     Gli elementi nella raccolta non è in modo da formare un singolo albero di incorporamento.  
  
     Per definire una relazione che è possibile usare unità di importazione, creare due classi di dominio e creare la relazione tra di essi.  
  
     È consigliabile impostare il **modificatore di ereditarietà** delle classi di dominio per `Abstract`.  
  
3. È possibile aggiungere gli elementi che definiscono in Esplora DSL, ad esempio i generatori di connessioni.  
  
4. È possibile aggiungere personalizzazioni che richiedono codice aggiuntivo, ad esempio i vincoli di convalida.  
  
5. Fare clic su **Trasforma tutti i modelli**.  
  
6. Compilare il progetto.  
  
7. Quando si distribuisce il linguaggio DSL per uso ad altri utenti, è necessario specificare sia l'assembly compilato (DLL) e il file `DslDefinition.dsl`. È possibile trovare l'assembly compilato in una cartella sotto `Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Per importare una libreria DSL  
  
1. In un'altra definizione DSL, nella **DSL Explorer**, fare doppio clic la classe radice del DSL e quindi fare clic su **Aggiungi nuova importazione di DslLibrary**.  
  
2. Nella finestra Proprietà impostare il **percorso File** della libreria. È possibile usare un percorso assoluto o relativo.  
  
    La libreria importata viene visualizzato in Esplora DSL, in modalità di sola lettura.  
  
3. È possibile utilizzare le classi importate come classi di base. Creare una classe di dominio nel DSL l'importazione e nelle proprietà della finestra, impostare **classe di base** a una classe importata.  
  
4. Fare clic su Trasforma tutti i modelli.  
  
5. Aggiungere al progetto DSL un riferimento all'assembly (DLL) che è stato compilato dal progetto di libreria DSL.  
  
6. Compilare la soluzione.  
  
   Una libreria DSL è possibile importare altre librerie. Quando si importa una libreria, in DSL Explorer vengono visualizzati automaticamente anche le relative importazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
