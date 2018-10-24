---
title: 'Area di test 5: Modifica controllo del codice sorgente | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed7093d50290c4c0612faf6c7691f90e62a08267
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847357"
---
# <a name="test-area-5-change-source-control"></a>Area di test 5: Modificare il controllo del codice sorgente
Quest'area del plug-in test di controllo del codice sorgente illustra la modifica il controllo del codice sorgente tramite il **Modifica controllo del codice sorgente** comando.  

 **Modifica controllo del codice sorgente** comando fornisce quattro funzioni di base per l'utente:  

- **Binding:**  

   Consente a un utente stabilire o ristabilire un collegamento di controllo di origine tra una soluzione/progetto e l'archivio delle versioni.  

- **Annullamento del binding:**  

   Rimuove una progetto/soluzione dal controllo del codice sorgente in una singola connessione.  

- **Connettere/disconnettere:**  

  Attiva o disattiva la stato connesso o non in linea della soluzione controllato, come illustrato nella zona 3. Per altre informazioni, vedere [Test zona 3: estrarre o annullare l'estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  

## <a name="command-menu-access"></a>Accesso a comandi di Menu  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] percorso menu ambiente di sviluppo integrato è utilizzato nei test case.  

 Modifica controllo del codice:**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**.  

## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case per il **Modifica controllo del codice sorgente** comando area di test.  

### <a name="case-5a-bind"></a>Caso 5a: eseguire l'associazione  
 Binding consente all'utente di aggiungere le informazioni sul controllo codice sorgente per i progetti selezionati e le soluzioni. L'utente è in genere viene richiesto di identificare un progetto nel controllo del codice sorgente in cui questi devono essere aggiunti. L'utente non può creare un nuovo progetto nel controllo del codice sorgente come parte di questa operazione (a contrasto elevato con Aggiungi al controllo del codice sorgente).  


| Operazione | Passi del test | Per verificare i risultati previsti |
| - | - | - |
| Binding a percorso vuoto | 1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire **Modifica controllo del codice sorgente** finestra di dialogo (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**).<br />4.  Fare clic su **disassociare**.<br />5.  Se viene visualizzata, accettare la finestra di dialogo di avviso.<br />6.  Selezionare tutti gli elementi.<br />7.  Fare clic su **associare**.<br />8.  Selezionare un percorso vuoto in un archivio di controllo di origine.<br />9. Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />10. Fare clic su **ontinua con le associazioni** nella finestra di dialogo di conferma.<br />11. Fare clic su **OK** nella finestra di dialogo di avviso se viene visualizzato.<br />12. Archivia i file. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />13. Aprire soluzioni dal controllo del codice sorgente in un nuovo percorso. | `Result from Step 12:`<br /><br /> Soluzioni e progetti sono associate a e scritti nella destinazione di nuovo nell'archivio delle versioni.<br /><br /> Vengono archiviati i file di soluzione e progetto.<br /><br /> Gerarchia del progetto archivio versione corrisponde alla gerarchia di cartelle del progetto su disco.<br /><br /> `Result from Step 13:`<br /><br /> Vengono scaricati tutti gli elementi di progetto. |
| Binding a percorso che è sincronizzato con client | 1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Creare un duplicato del progetto e soluzione nell'archivio delle versioni (condividere e creare un ramo se si usa [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Aprire **Modifica controllo del codice sorgente** finestra di dialogo (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**).<br />5.  Dissocia tutti.<br />6.  Fare clic su **OK** per chiudere **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />7.  Riaprire **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />8.  Selezionare tutto.<br />9. Fare clic su **associare**.<br />10. Selezionare il percorso della soluzione e progetto sottoposto a branching (dal passaggio 3)<br />11. Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />12. Ottenere più recente in modo ricorsivo per tutti gli elementi. | Contenuto del file dopo get esattamente come prima get. |
| Binding a percorso che non è sincronizzato con client | 1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Creare un duplicato del progetto e soluzione nell'archivio delle versioni (condividere e creare un ramo se si usa [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Modificare i file nel progetto sottoposto a branching nell'archivio delle versioni.<br />5.  Aprire **Modifica controllo del codice sorgente** finestra di dialogo (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**).<br />6.  Dissocia tutti.<br />7.  Fare clic su **OK** per chiudere **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />8.  Riaprire **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />9. Selezionare tutto.<br />10. Fare clic su **associare**.<br />11. Passare a un ramo di posizione per la soluzione e progetto.<br />12. Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />13. Se viene visualizzata, accettare la finestra di dialogo di avviso.<br />14. Ottenere ricorsivo più recente per tutti gli elementi. | I file che sono stati modificati nel passaggio 4 vengono modificati anche in locale. |
| Associare soluzione mai sotto il controllo del codice sorgente | 1.  Creare una cartella vuota nel controllo del codice sorgente.<br />2.  Creare un progetto client.<br />3.  Aprire **Modifica controllo del codice sorgente** finestra di dialogo (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**).<br />4.  Associare la soluzione in un percorso vuoto nel controllo del codice sorgente.<br />5.  Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />6.  Fare clic su **ontinua con le associazioni** nella finestra di dialogo di conferma.<br />7.  Fare clic su **OK** nella finestra di dialogo di avviso se viene visualizzato. | Soluzione viene aggiunta al controllo del codice sorgente.<br /><br /> Soluzioni e progetti sono stati estratti. |
| Annullare l'associazione | 1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4.  Dissocia tutti.<br />5.  Fare clic su **OK** per chiudere la finestra di dialogo. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />6.  Riaprire il **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />7.  Eseguire l'associazione alla posizione non correlati.<br />8.  Fare clic su **annullare**. | `Result from Step 5:`<br /><br /> La soluzione non è più in controllo del codice sorgente<br /><br /> `Result from Step 8:`<br /><br /> Soluzione è ancora non in controllo del codice sorgente. |

### <a name="case-5b-unbind"></a>Caso 5b: separazione  
 Dissocia le informazioni sul controllo codice sorgente rimuove da progetti e la propria soluzione. La soluzione e progetti interessati si basano su una combinazione di selezione dell'utente e come gli elementi sono stati aggiunti al controllo del codice sorgente.  

|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Annullamento del binding soluzione contenente un unico File System o progetto Web IIS locale e il progetto client|1.  Creare un File System o un progetto Web IIS locale.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un nuovo progetto di client per la soluzione.<br />4.  Se richiesto, accettare controllare della soluzione.<br />5.  Aprire il **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />6.  Fare clic su **disassociare**.<br />7.  Fare clic su **OK** per chiudere la finestra di dialogo.<br />8.  Tenta di estrarre soluzioni, progetti, elementi di soluzione, gli elementi del progetto.|Soluzioni e progetti non sono sotto controllo del codice sorgente.<br /><br /> Non vengono visualizzati i comandi di menu di controllo di origine.|  
|Annullare l'associazione Cancel|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire il **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />4.  Fare clic su **disassociare tutti**.<br />5.  Fare clic su **annullare**.|Soluzione consiste nel controllo del codice sorgente.|  

### <a name="case-5c-rebind"></a>Caso 5C: Rebind  
 Riassociazione è semplicemente una combinazione di separazione e bind, ovvero il processo di progetto o soluzione che era in precedenza nel controllo del codice sorgente ed è stato dissociato la riassociazione.  

|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Riassociare la soluzione e progetti senza chiudere il **Modifica controllo del codice sorgente** nella finestra di dialogo|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire il **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />4.  Fare clic su **disassociare**.<br />5.  Selezionare tutte le righe.<br />6.  Fare clic su **associare**.<br />7.  Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />8.  Se richiesto, accettare checkout.|Soluzioni e progetti sottoposti al controllo del codice sorgente.|  
|Riassociare progetto solo senza chiudere **Modifica controllo del codice sorgente** nella finestra di dialogo|1.  Creare un progetto.<br />2.  Aggiungere solo il progetto all'uso di controllo di origine (File -> origine controllo -> Aggiungi progetti selezionati a controllo del codice sorgente.<br />3.  Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4.  Rimuovere il binding solo il progetto.<br />5.  Eseguire l'associazione solo il progetto.|La soluzione rimane non controllata.<br /><br /> Progetto rimane controllato.|  
|Riassocia soluzione solo senza chiudere **Modifica controllo del codice sorgente** nella finestra di dialogo|1.  Creare un progetto.<br />2.  Aggiungere solo la soluzione al controllo di origine usando (**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**.<br />3.  Aprire il **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />4.  Annullare l'associazione solo la soluzione (non si chiude **Modifica controllo del codice sorgente** nella finestra di dialogo.)<br />5.  Eseguire l'associazione solo la soluzione.<br />6.  Fare clic su **OK** per chiudere la finestra di dialogo.<br />7.  Estrarre soluzioni e gli elementi di soluzione (se presente.)|La soluzione rimane controllata.<br /><br /> Progetto rimane non controllato.|  
|Riassocia soluzione/progetto solo quando è nella stessa directory|1.  Creare un progetto.<br />2.  Aggiungere solo il progetto al controllo di origine usando (**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**.<br />3.  Chiudere la soluzione.<br />4.  Creare una nuova soluzione con almeno due progetti.<br />5.  Aggiungere la soluzione al controllo del codice sorgente.<br />6.  Aggiungere il progetto creato nel passaggio 1 dal controllo del codice sorgente.<br />7.  Se richiesto, accettare l'estrazione della soluzione.<br />8.  Archiviare l'intera soluzione.<br />9. Aprire il **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />10. Selezionare il progetto aggiunto (dal passaggio 6) e fare clic su **Dissocia**.<br />11. Fare clic su **OK** per chiudere la finestra di dialogo.<br />12. Se richiesto, accettare il checkout.<br />13. Riaprire **Modifica controllo del codice sorgente** nella finestra di dialogo.<br />14. Selezionare il progetto aggiunto (dal passaggio 6) e fare clic su **associare**.<br />15. Selezionare il percorso originale.|Soluzioni e progetti di rimangano controllati.|  

## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)