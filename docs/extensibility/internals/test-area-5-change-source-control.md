---
title: 'Area di test 5: modificare il controllo del codice sorgente | Microsoft Docs'
description: Questa area di test del plug-in del controllo del codice sorgente copre la modifica del controllo del codice sorgente tramite il comando modifica controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44647781b8f7605a59fba5d9249b6a7165c0e27e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073404"
---
# <a name="test-area-5-change-source-control"></a>Area di test 5: Modificare il controllo del codice sorgente
Questa area di test del plug-in del controllo del codice sorgente copre la modifica del controllo del codice sorgente tramite il comando **modifica controllo del codice sorgente** .

 Il comando **modifica controllo del codice sorgente** fornisce quattro funzioni di base per l'utente:

- **Associare**

   Consente a un utente di stabilire o ristabilire un collegamento al controllo del codice sorgente tra una soluzione o un progetto e l'archivio versioni.

- **Disassociare**

   Rimuove un progetto o una soluzione dal controllo del codice sorgente per ogni singola connessione.

- **Connetti/Disconnetti:**

  Consente di impostare lo stato connesso o offline della soluzione controllata, che viene analizzata nell'area 3. Per ulteriori informazioni, vedere [area di test 3: Estrai/Annulla estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Nei test case viene utilizzato il seguente percorso del menu Integrated Development Environment.

 Modificare il controllo del codice sorgente:**file**, **controllo del codice sorgente**, **modifica controllo del codice sorgente**.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati i test case specifici per l'area di test del comando **modifica controllo del codice sorgente** .

### <a name="case-5a-bind"></a>Caso 5a: binding
 Binding consente all'utente di aggiungere informazioni di controllo del codice sorgente ai progetti e alle soluzioni selezionate. Viene in genere richiesto all'utente di identificare un progetto nel controllo del codice sorgente a cui devono essere aggiunti. L'utente non può creare un nuovo progetto nel controllo del codice sorgente come parte di questa operazione (a differenza di Aggiungi al controllo del codice sorgente).

| Azione | Passi del test | Risultati previsti da verificare |
| - | - | - |
| Associa a percorso vuoto | 1. creare un progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo **modifica controllo del codice sorgente** (**file**, **controllo del codice sorgente**, **modifica controllo del codice sorgente**).<br />4. fare clic su **Annulla binding**.<br />5. finestra di dialogo accetta avviso se visualizzata.<br />6. Selezionare tutti gli elementi.<br />7. fare clic su **Bind**.<br />8. individuare un percorso vuoto in un archivio del controllo del codice sorgente.<br />9. fare clic su **OK** per chiudere la finestra di dialogo **modifica controllo del codice sorgente** .<br />10. fare clic su **continua con questi binding** nella finestra di dialogo di conferma.<br />11. fare clic su **OK** nella finestra di dialogo di avviso, se visualizzata.<br />12. archiviare tutti gli elementi. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />13. Aprire la soluzione dal controllo del codice sorgente in una nuova posizione. | `Result from Step 12:`<br /><br /> La soluzione e il progetto vengono associati e scritti nella nuova destinazione nell'archivio delle versioni.<br /><br /> I file della soluzione e del progetto vengono archiviati.<br /><br /> La gerarchia del progetto Archivio versioni corrisponde alla gerarchia di cartelle del progetto su disco.<br /><br /> `Result from Step 13:`<br /><br /> Tutti gli elementi del progetto vengono scaricati. |
| Associa a percorso sincronizzato con il client | 1. creare un progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. creare un duplicato della soluzione e del progetto nell'archivio delle versioni (condivisione e ramo se si usa [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. Aprire la finestra di dialogo **modifica controllo del codice sorgente** (**file**, **controllo del codice sorgente**, **modifica controllo del codice sorgente**).<br />5. annullare l'associazione di tutti.<br />6. fare clic su **OK** per chiudere la finestra di dialogo **modifica controllo del codice sorgente** .<br />7. riaprire la finestra di dialogo **modifica controllo del codice sorgente** .<br />8. Selezionare tutti.<br />9. fare clic su **Bind**.<br />10. passare alla posizione sottoposta a branching della soluzione e del progetto (dal passaggio 3)<br />11. fare clic su **OK** per chiudere la finestra di dialogo **modifica controllo del codice sorgente** .<br />12. ottenere la versione più recente in modo ricorsivo per tutti gli elementi. | Il contenuto del file dopo l'ottenimento è identico a quello precedente a Get. |
| Associa a percorso non sincronizzato con il client | 1. creare un progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. creare un duplicato della soluzione e del progetto nell'archivio delle versioni (condivisione e ramo se si usa [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. modificare i file nel progetto sottoposto a branching nell'archivio delle versioni.<br />5. Aprire la finestra di dialogo **modifica controllo del codice sorgente** (**file**, **controllo del codice sorgente**, **modifica controllo del codice sorgente**).<br />6. annullare l'associazione di tutti.<br />7. fare clic su **OK** per chiudere la finestra di dialogo **modifica controllo del codice sorgente** .<br />8. riaprire la finestra di dialogo **modifica controllo del codice sorgente** .<br />9. Selezionare tutti.<br />10. fare clic su **Bind**.<br />11. passare alla posizione sottoposta a branching per la soluzione e il progetto.<br />12. fare clic su **OK** per chiudere la finestra di dialogo **modifica controllo del codice sorgente** .<br />13. finestra di dialogo accetta avviso se visualizzata.<br />14. ottenere la versione più recente ricorsiva per tutti gli elementi. | Anche i file modificati nel passaggio 4 vengono modificati localmente. |
| Associare una soluzione che non era mai sotto il controllo del codice sorgente | 1. creare una cartella vuota nel controllo del codice sorgente.<br />2. creare un progetto client.<br />3. Aprire la finestra di dialogo **modifica controllo del codice sorgente** (**file**, **controllo del codice sorgente**, **modifica controllo del codice sorgente**).<br />4. associare la soluzione a un percorso vuoto nel controllo del codice sorgente.<br />5. fare clic su **OK** per chiudere la finestra di dialogo **modifica controllo del codice sorgente** .<br />6. fare clic su **continua con questi binding** nella finestra di dialogo di conferma.<br />7. fare clic su **OK** nella finestra di dialogo di avviso, se visualizzata. | La soluzione viene aggiunta al controllo del codice sorgente.<br /><br /> La soluzione e il progetto sono estratti. |
| Annulla binding | 1. creare un progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4. annullare l'associazione di tutti.<br />5. fare clic sul pulsante **OK** per chiudere la finestra di dialogo. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />6. riaprire la finestra di dialogo **modifica controllo del codice sorgente** .<br />7. associarlo a un percorso non correlato.<br />8. fare clic su **Annulla**. | `Result from Step 5:`<br /><br /> La soluzione non è più disponibile nel controllo del codice sorgente<br /><br /> `Result from Step 8:`<br /><br /> La soluzione non è ancora sotto il controllo del codice sorgente. |

### <a name="case-5b-unbind"></a>Caso 5b: annullamento dell'associazione
 Annulla binding rimuove le informazioni di controllo del codice sorgente dai progetti e dalla relativa soluzione. I progetti e la soluzione interessati sono basati su una combinazione di selezione dell'utente e su come gli elementi sono stati aggiunti al controllo del codice sorgente.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Separa la soluzione contenente un file System o un progetto Web IIS locale e un progetto client|1. creare un file System o un progetto Web IIS locale.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. aggiungere un nuovo progetto client alla soluzione.<br />4. se richiesto, confermare l'estrazione della soluzione.<br />5. Aprire la finestra di dialogo **modifica controllo del codice sorgente** .<br />6. fare clic su **Annulla binding**.<br />7. fare clic su **OK** per chiudere la finestra di dialogo.<br />8. provare a estrarre la soluzione, il progetto, gli elementi della soluzione, gli elementi del progetto.|La soluzione e i progetti non sono inclusi nel controllo del codice sorgente.<br /><br /> I comandi del menu del controllo del codice sorgente non vengono visualizzati.|
|Annulla disassociazione|1. creare un progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo **modifica controllo del codice sorgente** .<br />4. fare clic su **Annulla binding tutti**.<br />5. fare clic su **Annulla**.|La soluzione è sotto il controllo del codice sorgente.|

### <a name="case-5c-rebind"></a>Caso 5C: riassociazione
 Rebind è semplicemente una combinazione di UNBIND e BIND, ovvero il processo di riassociazione di un progetto o di una soluzione precedentemente sotto il controllo del codice sorgente ed è stato non associato.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Riassocia la soluzione e i progetti senza chiudere la finestra di dialogo **modifica controllo del codice sorgente**|1. creare un progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo **modifica controllo del codice sorgente** .<br />4. fare clic su **Annulla binding**.<br />5. Selezionare tutte le righe.<br />6. fare clic su **Bind**.<br />7. fare clic su **OK** per chiudere la finestra di dialogo **modifica controllo del codice sorgente** .<br />8. se richiesto, accettare il checkout.|La soluzione e il progetto sono inclusi nel controllo del codice sorgente.|
|Riassocia solo il progetto senza chiudere la finestra di dialogo **modifica controllo del codice sorgente**|1. creare un progetto.<br />2. aggiungere solo il progetto al controllo del codice sorgente usando (controllo del codice sorgente >file->aggiungere progetti selezionati al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4. annullare l'associazione solo del progetto.<br />5. associare solo il progetto.|La soluzione rimane non controllata.<br /><br /> Il progetto rimane controllato.|
|Riassocia solo la soluzione senza chiudere la finestra di dialogo **modifica controllo del codice sorgente**|1. creare un progetto.<br />2. aggiungere solo la soluzione al controllo del codice sorgente usando (**file**, **controllo del codice sorgente**, **aggiungere progetti selezionati al controllo del codice sorgente**.<br />3. Aprire la finestra di dialogo **modifica controllo del codice sorgente** .<br />4. annullare l'associazione solo della soluzione (non chiudere la finestra di dialogo **modifica controllo del codice sorgente** ).<br />5. associare solo la soluzione.<br />6. fare clic su **OK** per chiudere la finestra di dialogo.<br />7. estrarre gli elementi della soluzione e della soluzione (se presenti).|La soluzione rimane controllata.<br /><br /> Il progetto rimane incontrollato.|
|Riassocia soluzione/progetto solo quando nella stessa directory|1. creare un progetto.<br />2. aggiungere solo il progetto al controllo del codice sorgente usando (**file**, **controllo del codice sorgente**, **Aggiungi progetti selezionati al controllo del codice sorgente**.<br />3. chiudere la soluzione.<br />4. creare una nuova soluzione con almeno due progetti.<br />5. aggiungere la soluzione al controllo del codice sorgente.<br />6. aggiungere il progetto creato nel passaggio 1 dal controllo del codice sorgente.<br />7. se richiesto, accettare il checkout della soluzione.<br />8. archiviare l'intera soluzione.<br />9. Aprire la finestra di dialogo **modifica controllo del codice sorgente** .<br />10. Selezionare il progetto aggiunto (dal passaggio 6) e fare clic su **Annulla binding**.<br />11. fare clic su **OK** per chiudere la finestra di dialogo.<br />12. se richiesto, accettare il checkout.<br />13. riaprire la finestra di dialogo **modifica controllo del codice sorgente** .<br />14. Selezionare il progetto aggiunto (dal passaggio 6) e fare clic su **associa**.<br />15. Selezionare la posizione originale.|La soluzione e i progetti rimangono controllati.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
