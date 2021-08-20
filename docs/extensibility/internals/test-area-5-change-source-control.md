---
title: 'Area di test 5: Modificare il controllo del codice sorgente | Microsoft Docs'
description: Questa area di test del plug-in del controllo del codice sorgente illustra la modifica del controllo del codice sorgente tramite il comando Modifica controllo del codice sorgente.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 24cbcc50b3641bc62242ee7216d6ce4c1f290efd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158775"
---
# <a name="test-area-5-change-source-control"></a>Area di test 5: Modificare il controllo del codice sorgente
Questa area di test del plug-in del controllo del codice sorgente illustra la modifica del controllo del codice sorgente tramite **il comando Cambia controllo del codice sorgente.**

 **Il comando Change Source Control** fornisce quattro funzioni di base per l'utente:

- **Associare:**

   Consente a un utente di stabilire o ristabilire un collegamento al controllo del codice sorgente tra una soluzione o un progetto e l'archivio delle versioni.

- **Separare:**

   Rimuove un progetto/soluzione dal controllo del codice sorgente per ogni connessione.

- **Connessione/Disconnetti:**

  Attiva o disattiva lo stato connesso o offline della soluzione controllata, come descritto nell'area 3. Per altre informazioni, vedere [Area di test 3: estrazione/annullamento dell'estrazione.](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

## <a name="command-menu-access"></a>Accesso al menu di comando
 Nei test case viene usato il percorso di menu dell'ambiente di sviluppo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrato seguente.

 Modifica controllo del codice sorgente:**File**, **Controllo del codice sorgente**, **Modifica controllo del codice sorgente**.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati test case specifici per l'area di test del comando **Cambia controllo** del codice sorgente.

### <a name="case-5a-bind"></a>Caso 5a: Associare
 L'associazione consente all'utente di aggiungere informazioni sul controllo del codice sorgente ai progetti e alle soluzioni selezionati. All'utente viene in genere richiesto di identificare un progetto nel controllo del codice sorgente a cui devono essere aggiunti. L'utente non può creare un nuovo progetto nel controllo del codice sorgente come parte di questa operazione (a differenza di Aggiungi al controllo del codice sorgente).

| Azione | Passaggi di test | Risultati previsti da verificare |
| - | - | - |
| Eseguire l'associazione a una posizione vuota | 1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la **finestra di dialogo Modifica controllo** del codice sorgente (**File**, Controllo del **codice sorgente**, **Modifica controllo del codice sorgente**).<br />4. Fare clic **su Annulla associazione**.<br />5. Accettare la finestra di dialogo di avviso, se visualizzata.<br />6. Selezionare tutti gli elementi.<br />7. Fare clic **su Associa**.<br />8. Passare a un percorso vuoto in un archivio del controllo del codice sorgente.<br />9. Fare clic **su OK** per chiudere la finestra di dialogo **Modifica controllo** del codice sorgente .<br />10. Fare clic **su Continua con queste associazioni nella finestra** di dialogo di conferma.<br />11. Fare clic **su OK** nella finestra di dialogo di avviso, se visualizzata.<br />12. Archiviare tutto. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />13. Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso. | `Result from Step 12:`<br /><br /> La soluzione e il progetto sono associati e scritti nella nuova destinazione nell'archivio versioni.<br /><br /> I file di soluzione e di progetto vengono archiviati.<br /><br /> La gerarchia del progetto dell'archivio versioni corrisponde alla gerarchia di cartelle del progetto su disco.<br /><br /> `Result from Step 13:`<br /><br /> Vengono scaricati tutti gli elementi del progetto. |
| Eseguire il binding alla posizione sincronizzata con il client | 1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Creare un duplicato della soluzione e del progetto nell'archivio delle versioni (Condivisione e ramo se si usa [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. Aprire la **finestra di dialogo Modifica controllo** del codice sorgente (**File**, Controllo del **codice sorgente**, **Modifica controllo del codice sorgente**).<br />5. Annullare l'associazione di tutti.<br />6. Fare clic **su OK** per chiudere la finestra di dialogo **Modifica controllo** del codice sorgente.<br />7. **Riaprire la finestra di dialogo Modifica controllo** del codice sorgente.<br />8. Selezionare tutto.<br />9. Fare clic **su Associa**.<br />10. Passare al percorso con ramo della soluzione e del progetto (dal passaggio 3)<br />11. Fare clic **su OK** per chiudere la finestra di dialogo **Modifica controllo** del codice sorgente .<br />12. Ottenere l'ultima versione in modo ricorsivo per tutti gli elementi. | Il contenuto del file dopo il metodo get è lo stesso di prima di get. |
| Eseguire l'associazione alla posizione non sincronizzata con il client | 1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Creare un duplicato della soluzione e del progetto nell'archivio delle versioni (Condivisione e ramo se si usa [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. Modificare i file nel progetto con ramo nell'archivio delle versioni.<br />5. Aprire la **finestra di dialogo Modifica controllo** del codice sorgente (**File**, Controllo del **codice sorgente**, **Modifica controllo del codice sorgente**).<br />6. Annullare l'associazione di tutti.<br />7. Fare clic **su OK** per chiudere la finestra di dialogo **Modifica controllo** del codice sorgente .<br />8. **Riaprire la finestra di dialogo Modifica controllo** del codice sorgente.<br />9. Selezionare tutto.<br />10. Fare clic **su Associa**.<br />11. Passare al percorso con ramo per la soluzione e il progetto.<br />12. Fare clic **su OK** per chiudere la finestra di dialogo **Modifica controllo** del codice sorgente .<br />13. Accettare la finestra di dialogo Avviso, se visualizzata.<br />14. Ottenere l'ultima ricorsiva per tutti gli elementi. | Anche i file modificati nel passaggio 4 vengono modificati in locale. |
| Associare una soluzione che non è mai stata sotto controllo del codice sorgente | 1. Creare una cartella vuota nel controllo del codice sorgente.<br />2. Creare un progetto client.<br />3. Aprire la **finestra di dialogo Modifica controllo** del codice sorgente (**File**, Controllo del **codice sorgente**, **Modifica controllo del codice sorgente**).<br />4. Associare la soluzione a una posizione vuota nel controllo del codice sorgente.<br />5. Fare clic **su OK** per chiudere la finestra di dialogo **Modifica controllo** del codice sorgente .<br />6. Fare **clic su Continua con queste associazioni nella** finestra di dialogo di conferma.<br />7. Fare clic **su OK** nella finestra di dialogo di avviso, se visualizzata. | La soluzione viene aggiunta al controllo del codice sorgente.<br /><br /> La soluzione e il progetto vengono estratti. |
| Annullare l'associazione | 1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo Modifica controllo del codice sorgente .<br />4. Annullare l'associazione di tutti.<br />5. Fare **clic su OK** per chiudere la finestra di dialogo. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />6. Riaprire la **finestra di dialogo Modifica controllo** del codice sorgente.<br />7. Eseguire il binding a una posizione non correlata.<br />8. Fare clic su **Annulla.** | `Result from Step 5:`<br /><br /> La soluzione non è più sotto controllo del codice sorgente<br /><br /> `Result from Step 8:`<br /><br /> La soluzione non è ancora in fase di controllo del codice sorgente. |

### <a name="case-5b-unbind"></a>Caso 5b: Annullare l'associazione
 Unbind rimuove le informazioni sul controllo del codice sorgente dai progetti e dalla relativa soluzione. I progetti e la soluzione interessati si basano su una combinazione di selezione dell'utente e sul modo in cui gli elementi sono stati aggiunti al controllo del codice sorgente.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Soluzione disassociata contenente un file system o un progetto Web IIS locale e un progetto client|1. Creare un file system o un progetto Web IIS locale.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un nuovo progetto client alla soluzione.<br />4. Accettare l'estrazione della soluzione, se richiesto.<br />5. Aprire la **finestra di dialogo Modifica controllo** del codice sorgente .<br />6. Fare clic **su Annulla associazione**.<br />7. Fare clic **su OK** per chiudere la finestra di dialogo.<br />8. Provare a estrarre soluzioni, progetti, elementi di soluzione, elementi di progetto.|La soluzione e i progetti NON sono sotto controllo del codice sorgente.<br /><br /> I comandi di menu del controllo del codice sorgente non vengono visualizzati.|
|Annullare l'associazione|1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la **finestra di dialogo Modifica controllo** del codice sorgente .<br />4. Fare clic **su Annulla associazione di tutti**.<br />5. Fare clic su **Annulla.**|La soluzione è sotto controllo del codice sorgente.|

### <a name="case-5c-rebind"></a>Caso 5c: Riassociazione
 Il riassociazione è semplicemente una combinazione di associazione e associazione non associata, ovvero il processo di riassociazione di un progetto/soluzione precedentemente sotto controllo del codice sorgente e non associato.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Riassociare soluzioni e progetti senza chiudere la **finestra di dialogo Modifica controllo** del codice sorgente|1. Creare un progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aprire la **finestra di dialogo Modifica controllo** del codice sorgente .<br />4. Fare clic **su Annulla associazione**.<br />5. Selezionare tutte le righe.<br />6. Fare clic **su Associa**.<br />7. Fare clic **su OK** per chiudere la finestra di dialogo **Modifica controllo** del codice sorgente .<br />8. Accettare l'estrazione, se richiesto.|La soluzione e il progetto sono sotto controllo del codice sorgente.|
|Riassociare il progetto solo senza chiudere **la finestra di dialogo Modifica controllo del** codice sorgente|1. Creare un progetto.<br />2. Aggiungere solo il progetto al controllo del codice sorgente usando (File->Source Control->Aggiungi progetti selezionati al controllo del codice sorgente.<br />3. Aprire la finestra di dialogo Modifica controllo del codice sorgente .<br />4. Annullare l'associazione solo del progetto.<br />5. Associare solo il progetto.|La soluzione rimane incontrollato.<br /><br /> Project rimane controllato.|
|Riassociare la soluzione solo senza chiudere **la finestra di dialogo Modifica controllo del** codice sorgente|1. Creare un progetto.<br />2. Aggiungere solo la soluzione al controllo del codice sorgente usando (**File**, **Controllo del** codice sorgente , Aggiungi progetti selezionati al controllo del **codice sorgente**.<br />3. Aprire la **finestra di dialogo Modifica controllo** del codice sorgente .<br />4. Annullare l'associazione solo della soluzione (non chiudere la **finestra di** dialogo Modifica controllo del codice sorgente).<br />5. Associare solo la soluzione.<br />6. Fare **clic su OK** per chiudere la finestra di dialogo.<br />7. Controllare la soluzione e gli eventuali elementi della soluzione|La soluzione rimane controllata.<br /><br /> Project rimane incontrollato.|
|Riassociare soluzione/progetto solo quando si è nella stessa directory|1. Creare un progetto.<br />2. Aggiungere solo il progetto al controllo del codice sorgente usando (**File**, **Controllo del** codice sorgente , Aggiungi progetti selezionati al controllo del **codice sorgente**.<br />3. Chiudere la soluzione.<br />4. Creare una nuova soluzione con almeno due progetti.<br />5. Aggiungere la soluzione al controllo del codice sorgente.<br />6. Aggiungere il progetto creato nel passaggio 1 dal controllo del codice sorgente.<br />7. Accettare il pagamento della soluzione, se richiesto.<br />8. Archiviare l'intera soluzione.<br />9. Aprire la **finestra di dialogo Modifica controllo** del codice sorgente .<br />10. Selezionare il progetto aggiunto (nel passaggio 6) e fare clic su **Annulla associazione**.<br />11. Fare clic **su OK** per chiudere la finestra di dialogo.<br />12. Accettare il pagamento, se richiesto.<br />13. **Riaprire la finestra di dialogo Modifica controllo** del codice sorgente.<br />14. Selezionare il progetto aggiunto (nel passaggio 6) e fare clic su **Associa**.<br />15. Selezionare il percorso originale.|La soluzione e i progetti rimangono controllati.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
