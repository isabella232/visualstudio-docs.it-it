---
title: 'Area di test 5: Modifica del controllo del codice sorgente Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c0df31fbecd532e6a5f7f317730cd995cd8225
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704517"
---
# <a name="test-area-5-change-source-control"></a>Area di test 5: Modificare il controllo del codice sorgente
Questa area di test del plug-in del controllo del codice sorgente illustra la modifica del controllo del codice sorgente tramite il comando **Modifica controllo del codice sorgente.**

 **Il** comando Change Source Control fornisce quattro funzioni di base per l'utente:

- **Associare:**

   Consente a un utente di stabilire o ristabilire un collegamento del controllo del codice sorgente tra una soluzione/progetto e l'archivio versioni.

- **Separare:**

   Rimuove un progetto/soluzione dal controllo del codice sorgente in base alla connessione.

- **Connetti/Disconnetti:**

  Attiva/disattiva lo stato connesso o offline della soluzione controllata, descritta nell'Area 3. Per ulteriori informazioni, vedere [Area di test 3: Estrazione/annullamento dell'estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 Nei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] test case viene utilizzato il seguente percorso del menu dell'ambiente di sviluppo integrato.

 Modifica controllo del codice sorgente:**File**, **Controllo del codice sorgente**, Modifica controllo del codice **sorgente**.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati test case specifici per l'area di test del comando **Modifica controllo del codice sorgente.**

### <a name="case-5a-bind"></a>Caso 5a: Lega
 Bind consente all'utente di aggiungere informazioni sul controllo del codice sorgente ai progetti e alle soluzioni selezionati. All'utente viene in genere richiesto di identificare un progetto nel controllo del codice sorgente a cui devono essere aggiunti. L'utente non può creare un nuovo progetto nel controllo del codice sorgente come parte di questa operazione (a differenza di Aggiungi al controllo del codice sorgente).

| Azione | Passaggi del testTest Steps | Risultati previsti da verificare |
| - | - | - |
| Eseguire il binding in una posizione vuotaBind to empty location | 1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo **Modifica controllo del codice sorgente** (**File**, Controllo del **codice sorgente**, Modifica controllo del **codice sorgente**).<br />4. Fare clic su **Annulla binding**.<br />5. Accettare la finestra di dialogo di avviso se viene visualizzato.<br />6. Selezionare tutti gli elementi.<br />7. Fare clic su **Associa**.<br />8. Passare a un percorso vuoto in un archivio del controllo del codice sorgente.<br />9. Fare clic **su OK** per chiudere la finestra di dialogo Modifica controllo del **codice sorgente.**<br />10. Fare clic su **Continua con questi binding** nella finestra di dialogo di conferma.<br />11. Fare clic **su OK** nella finestra di dialogo di avviso se viene visualizzato.<br />12. Controlla tutto. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />13. Aprire la soluzione dal controllo del codice sorgente in una nuova posizione. | `Result from Step 12:`<br /><br /> Soluzione e progetto sono associati e scritti nella nuova destinazione nell'archivio versioni.<br /><br /> I file di soluzione e di progetto vengono archiviati.<br /><br /> La gerarchia del progetto dell'archivio versioni corrisponde alla gerarchia di cartelle del progetto su disco.<br /><br /> `Result from Step 13:`<br /><br /> Tutti gli elementi del progetto vengono scaricati. |
| Eseguire il binding a un percorso sincronizzato con il clientBind to location that is in sync with client | 1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Creare un duplicato della soluzione e del progetto [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]nell'archivio versioni (Share e Branch se using ).<br />4. Aprire la finestra di dialogo **Modifica controllo del codice sorgente** (**File**, Controllo del **codice sorgente**, Modifica controllo del **codice sorgente**).<br />5. Svincola tutto.<br />6. Fare clic **su OK** per chiudere la finestra di dialogo Modifica controllo del **codice sorgente.**<br />7. Riaprire la finestra di dialogo **Modifica controllo del codice sorgente.**<br />8. Selezionare tutto.<br />9. Fare clic su **Associa**.<br />10. Individuare il percorso ramificato della soluzione e del progetto (dal passaggio 3)<br />11. Fare clic **su OK** per chiudere la finestra di dialogo Modifica controllo del **codice sorgente.**<br />12. Ottenere più recente mente per tutti gli elementi. | Il contenuto del file dopo il get è lo stesso di prima del get. |
| Eseguire il binding a un percorso non sincronizzato con il clientBind to location that is out of sync with client | 1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Creare un duplicato della soluzione e del progetto [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]nell'archivio versioni (Share e Branch se using ).<br />4. Modificare i file nel progetto ramificato nell'archivio versioni.<br />5. Aprire la finestra di dialogo **Modifica controllo del codice sorgente** (**File**, Controllo del **codice sorgente**, Modifica controllo del **codice sorgente**).<br />6. Svincolare tutto.<br />7. Fare clic **su OK** per chiudere la finestra di dialogo Modifica controllo del **codice sorgente.**<br />8. Riaprire la finestra di dialogo **Modifica controllo del codice sorgente.**<br />9. Selezionare tutto.<br />10. Fare clic su **Associa**.<br />11. Passare al percorso ramificato per la soluzione e il progetto.<br />12. Fare clic **su OK** per chiudere la finestra di dialogo Modifica controllo del **codice sorgente.**<br />13. Accettare la finestra di dialogo Avviso se viene visualizzata.<br />14. Ottenere l'ultima ricorsiva per tutti gli elementi. | Anche i file modificati nel passaggio 4 vengono modificati localmente. |
| Associare una soluzione che non è mai stata sotto il controllo del codice sorgenteBind solution that was never under source control | 1. Creare una cartella vuota nel controllo del codice sorgente.<br />2. Creare un progetto client.<br />3. Aprire la finestra di dialogo **Modifica controllo del codice sorgente** (**File**, Controllo del **codice sorgente**, Modifica controllo del **codice sorgente**).<br />4. Associare la soluzione a un percorso vuoto nel controllo del codice sorgente.<br />5. Fare clic **su OK** per chiudere la finestra di dialogo Modifica controllo del **codice sorgente.**<br />6. Fare clic su **Continua con questi binding** nella finestra di dialogo di conferma.<br />7. Fare clic **su OK** nella finestra di dialogo di avviso se viene visualizzato. | La soluzione viene aggiunta al controllo del codice sorgente.<br /><br /> Soluzione e progetto sono estratti. |
| Annulla binding | 1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4. Svincola tutto.<br />5. Clic **OK** pulsante per chiudere la finestra di dialogo. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />6. Riaprire la finestra di dialogo **Modifica controllo del codice sorgente.**<br />7. Eseguire il binding a una posizione non correlata.<br />8. Fare clic su **Annulla**. | `Result from Step 5:`<br /><br /> La soluzione non è più sotto il controllo del codice sorgente<br /><br /> `Result from Step 8:`<br /><br /> La soluzione NON è ancora sotto il controllo del codice sorgente. |

### <a name="case-5b-unbind"></a>Caso 5b: Disassociazione
 L'annullamento dell'associazione rimuove le informazioni sul controllo del codice sorgente dai progetti e dalla relativa soluzione. I progetti e la soluzione interessati si basano su una combinazione di selezione dell'utente e su come gli elementi sono stati aggiunti al controllo del codice sorgente.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Unbind soluzione contenente un file system o un progetto Web IIS locale e un progetto client|1. Creare un file system o un progetto Web IIS locale.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un nuovo progetto client alla soluzione.<br />4. Se richiesto, accettare l'estrazione della soluzione.<br />5. Aprire la finestra di dialogo **Modifica controllo del codice sorgente.**<br />6. Fare clic su **Disassocia**.<br />7. Fare clic **su OK** per chiudere la finestra di dialogo.<br />8. Tentare di estrarre soluzione, progetto, elementi di soluzione, elementi di progetto.|Soluzione e progetti NON sono sotto controllo del codice sorgente.<br /><br /> I comandi del menu Controllo del codice sorgente non vengono visualizzati.|
|Annulla annullamento associazione|1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo **Modifica controllo del codice sorgente.**<br />4. Fare clic su **Disassocia tutto**.<br />5. Fare clic su **Annulla**.|La soluzione è sotto controllo del codice sorgente.|

### <a name="case-5c-rebind"></a>Caso 5c: Riassociare
 La riassociazione è semplicemente una combinazione di annullamento e associazione, ovvero il processo di riassociazione di un progetto/soluzione precedentemente in controllo del codice sorgente non associato.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Riassociare soluzioni e progetti senza chiudere la finestra di dialogo **Modifica controllo del codice sorgenteRebind** solution and projects without closing the Change Source Control dialog box|1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo **Modifica controllo del codice sorgente.**<br />4. Fare clic su **Annulla binding**.<br />5. Selezionare tutte le righe.<br />6. Fare clic su **Associa**.<br />7. Fare clic **su OK** per chiudere la finestra di dialogo Modifica controllo del **codice sorgente.**<br />8. Accettare il checkout se richiesto.|Soluzione e progetto sono sotto controllo del codice sorgente.|
|Riassocia progetto solo senza chiudere la finestra di dialogo **Modifica controllo del codice sorgente**|1. Creare un progetto.<br />2. Aggiungere solo il progetto al controllo del codice sorgente utilizzando (File->controllo del codice sorgente->Aggiungi progetti selezionati al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4. Annullare l'associazione solo al progetto.<br />5. Associare solo il progetto.|La soluzione rimane incontrollata.<br /><br /> Il progetto rimane controllato.|
|Riassocia soluzione solo senza chiudere la finestra di dialogo **Modifica controllo del codice sorgenteRebind** solution only without closing Change Source Control dialog box|1. Creare un progetto.<br />2. Aggiungere solo la soluzione al controllo del codice sorgente utilizzando (**File**, **Controllo del codice sorgente**, Aggiungi progetti selezionati al controllo del codice **sorgente**.<br />3. Aprire la finestra di dialogo **Modifica controllo del codice sorgente.**<br />4. Scollegare solo la soluzione (non chiudere la finestra di dialogo **Modifica controllo del codice sorgente).**<br />5. Associare solo la soluzione.<br />6. Fare clic **su OK** per chiudere la finestra di dialogo.<br />7. Estrarre gli elementi della soluzione e della soluzione (se presenti.)|La soluzione rimane controllata.<br /><br /> Il progetto rimane incontrollato.|
|Riassociare soluzione/progetto solo nella stessa directoryRebind solution/project only when in same directory|1. Creare un progetto.<br />2. Aggiungere solo il progetto al controllo del codice sorgente utilizzando (**File**, **Controllo del codice sorgente**, Aggiungi progetti selezionati al controllo del codice **sorgente**.<br />3. Chiudere la soluzione.<br />4. Creare una nuova soluzione con almeno due progetti.<br />5. Aggiungere la soluzione al controllo del codice sorgente.<br />6. Aggiungere il progetto creato nel passaggio 1 dal controllo del codice sorgente.<br />7. Accettare il checkout della soluzione, se richiesto.<br />8. Archiviare l'intera soluzione.<br />9. Aprire la finestra di dialogo **Modifica controllo del codice sorgente.**<br />10. Selezionare il progetto aggiunto (dal passaggio 6) e fare clic su **Annulla associazione**.<br />11. Fare clic **su OK** per chiudere la finestra di dialogo.<br />12. Accettare il checkout, se richiesto.<br />13. Riaprire la finestra di dialogo **Modifica controllo del codice sorgente.**<br />14. Selezionare il progetto aggiunto (dal passaggio 6) e fare clic su **Associa**.<br />15. Selezionare la posizione originale.|Soluzione e progetti rimangono controllati.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
