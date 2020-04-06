---
title: 'Area di prova 8: Commutazione plug-in Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704398"
---
# <a name="test-area-8-plug-in-switching"></a>Area di test 8: Cambio di plug-in
L'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE) dispone dell'interfaccia utente (UI) per modificare il plug-in del controllo del codice sorgente corrente. Questa area di test fornisce test case per il processo di selezione del plug-in da utilizzare per il controllo del codice sorgente della soluzione.

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 Nei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] test case vengono utilizzati i percorsi di menu dell'ambiente di sviluppo integrato seguenti.

- Plug-in controllo del **Tools** -> codice sorgente corrente:**Strumenti Opzioni Selezione** -> **plug-in****controllo** -> del codice sorgente .

- Modificare l'associazione del controllo del codice sorgente: Controllo**del codice sorgente** ->  **del file** -> **Modifica controllo del codice sorgente**...

## <a name="common-expected-behavior"></a>Comportamento previsto comuneCommon Expected Behavior
 La modifica del plug-in del controllo del codice sorgente per una soluzione è possibile senza uscire da Visual Studio o ricaricare la soluzione. Inoltre, il plug-in del controllo del codice sorgente corrente passa automaticamente a quello utilizzato da una soluzione quando tale soluzione viene caricata.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati i test case specifici per l'area di test di commutazione del plug-in.

### <a name="case-8a-automatic-change"></a>Caso 8a: Cambio automatico

#### <a name="expected-behavior"></a>Comportamento previsto
 Quando un utente carica una soluzione inserita nel controllo del codice sorgente, la soluzione viene caricata automaticamente e il plug-in del controllo del codice sorgente appropriato viene selezionato come corrente.

| Azione | Passaggi del testTest Steps | Risultati previsti da verificare |
| - | - | - |
| Modifica automatica del plug-in del controllo del codice sorgente | 1. Selezionare plug-in sottoposto a test come corrente **(Strumenti** -> **Opzioni** -> Selezione**plug-in****controllo** -> del codice sorgente .)<br />2. Creare un nuovo progetto.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Selezionare un altro plug-in (ad esempio, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5. Accettare il prompt della soluzione di scarico.<br />6. Riaprire la soluzione dal disco. | La soluzione viene aperta.<br /><br /> Plug-in sottoposto a test è il plug-in del controllo del codice sorgente corrente. |

### <a name="case-8b-solution-based-change"></a>Caso 8b: Modifica basata su soluzione

#### <a name="expected-behavior"></a>Comportamento previsto
 La soluzione può avere il plug-in del controllo del codice sorgente associato modificato.

| Azione | Passaggi del testTest Steps | Risultati previsti da verificare |
|----------------------------------| - | - |
| Modifica del plug-in per una soluzione | 1. Selezionare plug-in sottoposto a test come corrente **(Strumenti** -> **Opzioni Selezione** -> **plug-in****controllo** -> del codice sorgente ).<br />2. Creare un nuovo progetto e una nuova soluzione.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Annullare l'associazione della soluzione dal controllo del codice sorgente (utilizzando la finestra di dialogo **Modifica controllo del codice sorgente).**<br />5. Selezionare un altro plug-in (ad esempio, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6. Ricaricare la soluzione dal disco se scaricata.<br />7. Aggiungere la soluzione al controllo del codice sorgente.<br />8. Annullare l'associazione della soluzione dal controllo del codice sorgente (utilizzando la finestra di **dialogo Modifica controllo del codice sorgente).**<br />9. Selezionare nuovamente il plug-in sotto test.<br />10. Ricaricare la soluzione dal disco se scaricata.<br />11. Associare la soluzione al percorso originale (utilizzando la finestra di dialogo **Modifica controllo del codice sorgente).** | La soluzione viene aggiunta al controllo del codice sorgente utilizzando il plug-in selezionato. |

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
