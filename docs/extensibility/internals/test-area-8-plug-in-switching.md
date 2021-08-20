---
title: "Area di test 8: Passaggio da un plug-in all'| Microsoft Docs"
description: Questa area di test del controllo del codice sorgente fornisce test case per il processo di selezione del plug-in da usare per il controllo del codice sorgente della soluzione in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: de08444c91ed0ab9bebc828873b7485ba97e6584
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158632"
---
# <a name="test-area-8-plug-in-switching"></a>Area di test 8: Cambio di plug-in
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'ambiente di sviluppo integrato (IDE) include l'interfaccia utente per modificare il plug-in del controllo del codice sorgente corrente. Questa area di test fornisce test case per il processo di selezione del plug-in da usare per il controllo del codice sorgente della soluzione.

## <a name="command-menu-access"></a>Accesso al menu di comando
 Nei test case vengono usati i percorsi di menu dell'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato seguenti.

- Plug-in del controllo del codice sorgente corrente: **Strumenti**  ->  **Opzioni**  ->    ->  **Plug-in controllo del codice sorgente Selezione.**

- Modificare l'associazione del controllo del codice **sorgente: Controllo**  ->  **del codice sorgente file** Modifica controllo codice  ->  **sorgente**...

## <a name="common-expected-behavior"></a>Comportamento previsto comune
 La modifica del plug-in del controllo del codice sorgente per una soluzione è possibile senza uscire Visual Studio o ricaricare la soluzione. Inoltre, il plug-in del controllo del codice sorgente corrente cambia automaticamente in quello usato da una soluzione quando tale soluzione viene caricata.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati test case specifici per l'area di test di commutazione del plug-in.

### <a name="case-8a-automatic-change"></a>Caso 8a: Modifica automatica

#### <a name="expected-behavior"></a>Comportamento previsto
 Quando un utente carica una soluzione nel controllo del codice sorgente, la soluzione viene caricata automaticamente e il plug-in di controllo del codice sorgente appropriato viene selezionato come corrente.

| Azione | Passi del test | Risultati previsti da verificare |
| - | - | - |
| Modifica automatica del plug-in del controllo del codice sorgente | 1. Selezionare il plug-in sotto test come corrente **(Strumenti**  ->  **Opzioni**  ->    ->  **Selezione plug-in controllo del codice sorgente).**<br />2. Creare un nuovo progetto.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Selezionare un altro plug-in , ad esempio [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] .<br />5. Accettare la richiesta di scaricamento della soluzione.<br />6. Riaprire la soluzione dal disco. | La soluzione viene aperta.<br /><br /> Plug-in sotto test è il plug-in del controllo del codice sorgente corrente. |

### <a name="case-8b-solution-based-change"></a>Caso 8b: Modifica basata sulla soluzione

#### <a name="expected-behavior"></a>Comportamento previsto
 La soluzione può avere il plug-in del controllo del codice sorgente associato modificato.

| Azione | Passi del test | Risultati previsti da verificare |
|----------------------------------| - | - |
| Modifica del plug-in per una soluzione | 1. Selezionare il plug-in sotto test come corrente **(** Strumenti  ->  **Opzioni**  ->    ->  **Selezione plug-in controllo del codice sorgente**).<br />2. Creare un nuovo progetto e una nuova soluzione.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Disassociare la soluzione dal controllo del codice sorgente (usando la **finestra di dialogo** Modifica controllo del codice sorgente).<br />5. Selezionare un altro plug-in , ad esempio [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] .<br />6. Ricaricare la soluzione dal disco se scaricata.<br />7. Aggiungere la soluzione al controllo del codice sorgente.<br />8. Disassociare la soluzione dal controllo del codice sorgente (usando la **finestra di dialogo** Modifica controllo del codice sorgente).<br />9. Selezionare di nuovo il plug-in sotto test.<br />10. Ricaricare la soluzione dal disco se scaricata.<br />11. Associare la soluzione al percorso originale (usando la **finestra di dialogo** Modifica controllo del codice sorgente). | La soluzione viene aggiunta al controllo del codice sorgente usando il plug-in selezionato. |

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
