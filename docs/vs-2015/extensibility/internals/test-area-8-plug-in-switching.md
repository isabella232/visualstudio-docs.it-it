---
title: 'Area di test 8: cambio di plug-in | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90650b8b3c3432fce05b03a25033977e68f60fca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203116"
---
# <a name="test-area-8-plug-in-switching"></a>Area di test 8: Cambio di plug-in
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrated Development Environment (IDE) dispone dell'interfaccia utente per modificare il plug-in del controllo del codice sorgente corrente. Questa area di test fornisce i test case per il processo di selezione del plug-in da utilizzare per il controllo del codice sorgente della soluzione.  
  
## <a name="command-menu-access"></a>Accesso al menu dei comandi  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Nei test case vengono utilizzati i percorsi dei menu Integrated Development Environment seguenti.  
  
- Plug-in del controllo del codice sorgente corrente: **strumenti**  ->  **Opzioni Opzioni**  ->  **Source Control**  ->  **plug-in controllo del**codice sorgente.  
  
- Modificare l'associazione del controllo del codice sorgente: modificare il controllo **del codice sorgente**  ->  **Source Control**  ->  **Change Source Control**...  
  
## <a name="common-expected-behavior"></a>Comportamento previsto comune  
 È possibile modificare il plug-in del controllo del codice sorgente per una soluzione senza uscire da Visual Studio o ricaricare la soluzione. Inoltre, il plug-in del controllo del codice sorgente corrente viene automaticamente modificato in quello utilizzato da una soluzione quando viene caricata la soluzione.  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono riportati i test case specifici per l'area di test del commutatore plug-in.  
  
### <a name="case-8a-automatic-change"></a>Caso 8a: modifica automatica  
  
#### <a name="expected-behavior"></a>Comportamento previsto  
 Quando un utente carica una soluzione nel controllo del codice sorgente, la soluzione viene caricata automaticamente e il plug-in del controllo del codice sorgente appropriato viene selezionato come corrente.  
  
|Action|Passi del test|Risultati previsti da verificare|  
|------------|----------------|--------------------------------|  
|Modifica del plug-in del controllo del codice sorgente automatico|1. Selezionare il plug-in sottoposto a test come corrente (**strumenti**  ->  **Opzioni**  ->  **controllo del codice sorgente**  ->  **plug-in selezione**).<br />2. creare un nuovo progetto.<br />3. aggiungere la soluzione al controllo del codice sorgente.<br />4. Selezionare un altro plug-in, ad esempio [!INCLUDE[vsvss](../../includes/vsvss-md.md)] .<br />5. accettare la richiesta di scaricamento della soluzione.<br />6. riaprire la soluzione dal disco.|La soluzione è aperta.<br /><br /> Il plug-in sottoposto a test è il plug-in del controllo del codice sorgente corrente.|  
  
### <a name="case-8b-solution-based-change"></a>Caso 8b: modifica basata sulla soluzione  
  
#### <a name="expected-behavior"></a>Comportamento previsto  
 È possibile modificare il plug-in del controllo del codice sorgente associato alla soluzione.  
  
|Action|Passi del test|Risultati previsti da verificare|  
|------------|----------------|--------------------------------|  
|Modifica del plug-in per una soluzione|1. Selezionare il plug-in sottoposto a test come corrente (**strumenti**  ->  **Opzioni**  ->  **controllo del codice sorgente**  ->  **plug-in selezione**).<br />2. creare un nuovo progetto e una nuova soluzione.<br />3. aggiungere la soluzione al controllo del codice sorgente.<br />4. annullare l'associazione della soluzione dal controllo del codice sorgente usando la finestra di dialogo **modifica controllo del codice sorgente** .<br />5. Selezionare un altro plug-in, ad esempio [!INCLUDE[vsvss](../../includes/vsvss-md.md)] .<br />6. ricaricare la soluzione dal disco se scaricata.<br />7. aggiungere la soluzione al controllo del codice sorgente.<br />8. annullare l'associazione della soluzione dal controllo del codice sorgente usando la finestra di dialogo **modifica controllo del codice sorgente** .<br />9. Selezionare di nuovo il plug-in sottoposto a test.<br />10. ricaricare la soluzione dal disco se scaricata.<br />11. associare la soluzione al percorso originale (usando la finestra di dialogo **modifica controllo del codice sorgente** ).|La soluzione viene aggiunta al controllo del codice sorgente utilizzando il plug-in selezionato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
