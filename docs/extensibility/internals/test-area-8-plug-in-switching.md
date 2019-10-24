---
title: 'Area di test 8: cambio di plug-in | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb815a773351c1bb6212962a639e2758114a0e2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722427"
---
# <a name="test-area-8-plug-in-switching"></a>Area di test 8: Cambio di plug-in
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) dispone dell'interfaccia utente per modificare il plug-in del controllo del codice sorgente corrente. Questa area di test fornisce i test case per il processo di selezione del plug-in da utilizzare per il controllo del codice sorgente della soluzione.

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 Nei test case vengono utilizzati i seguenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment i percorsi dei menu.

- Plug-in del controllo del codice sorgente corrente: **strumenti**  -> **Opzioni**  -> **controllo del codice sorgente**  -> **Selezione plug-in**.

- Modifica associazione del controllo del codice sorgente: **File**  -> **controllo** del codice sorgente  -> **modificare il controllo del codice sorgente**...

## <a name="common-expected-behavior"></a>Comportamento previsto comune
 È possibile modificare il plug-in del controllo del codice sorgente per una soluzione senza uscire da Visual Studio o ricaricare la soluzione. Inoltre, il plug-in del controllo del codice sorgente corrente viene automaticamente modificato in quello utilizzato da una soluzione quando viene caricata la soluzione.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati i test case specifici per l'area di test del commutatore plug-in.

### <a name="case-8a-automatic-change"></a>Caso 8a: modifica automatica

#### <a name="expected-behavior"></a>Comportamento previsto
 Quando un utente carica una soluzione nel controllo del codice sorgente, la soluzione viene caricata automaticamente e il plug-in del controllo del codice sorgente appropriato viene selezionato come corrente.

| Operazione | Passi del test | Risultati previsti da verificare |
| - | - | - |
| Modifica del plug-in del controllo del codice sorgente automatico | 1. Selezionare il plug-in sottoposto a test come corrente (**strumenti**  -> **Opzioni**  -> **controllo del codice sorgente**  -> **Selezione plug-in**.)<br />2. creare un nuovo progetto.<br />3. aggiungere la soluzione al controllo del codice sorgente.<br />4. Selezionare un altro plug-in, ad esempio [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)].<br />5. accettare la richiesta di scaricamento della soluzione.<br />6. riaprire la soluzione dal disco. | La soluzione è aperta.<br /><br /> Il plug-in sottoposto a test è il plug-in del controllo del codice sorgente corrente. |

### <a name="case-8b-solution-based-change"></a>Caso 8b: modifica basata sulla soluzione

#### <a name="expected-behavior"></a>Comportamento previsto
 È possibile modificare il plug-in del controllo del codice sorgente associato alla soluzione.

| Operazione | Passi del test | Risultati previsti da verificare |
|----------------------------------| - | - |
| Modifica del plug-in per una soluzione | 1. Selezionare il plug-in sottoposto a test come corrente (**strumenti**  -> **Opzioni**  -> **controllo del codice sorgente**  -> **Selezione plug-in**).<br />2. creare un nuovo progetto e una nuova soluzione.<br />3. aggiungere la soluzione al controllo del codice sorgente.<br />4. annullare l'associazione della soluzione dal controllo del codice sorgente usando la finestra di dialogo **modifica controllo del codice sorgente** .<br />5. Selezionare un altro plug-in, ad esempio [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)].<br />6. ricaricare la soluzione dal disco se scaricata.<br />7. aggiungere la soluzione al controllo del codice sorgente.<br />8. annullare l'associazione della soluzione dal controllo del codice sorgente usando la finestra di dialogo **modifica controllo del codice sorgente** .<br />9. Selezionare di nuovo il plug-in sottoposto a test.<br />10. ricaricare la soluzione dal disco se scaricata.<br />11. associare la soluzione al percorso originale (usando la finestra di dialogo **modifica controllo del codice sorgente** ). | La soluzione viene aggiunta al controllo del codice sorgente utilizzando il plug-in selezionato. |

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)