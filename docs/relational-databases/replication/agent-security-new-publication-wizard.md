---
title: "Agent Security (New Publication Wizard)"
description: "Agent Security (New Publication Wizard)"
author: "MashaMSFT"
ms.author: "mathoma"
ms.date: "03/14/2017"
ms.service: sql
ms.subservice: replication
ms.topic: conceptual
ms.custom: updatefrequency5
f1_keywords:
  - "sql13.rep.agentsecurity.articles.f1"
monikerRange: "=azuresqldb-mi-current||>=sql-server-2016"
---
# Agent Security (New Publication Wizard)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  The **Agent Security** page allows you to specify the accounts under which the following agents run and make connections to the computers in a replication topology:  
  
-   The Snapshot Agent for all publications.  
  
-   The Log Reader Agent for all transactional publications.  
  
-   The Queue Reader Agent for transactional publications that allow updatable subscriptions. The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job for this agent is created if you specified **Transactional publication with updatable subscriptions** on the **Publication Type** page, regardless of the type of updatable subscriptions you use. For more information about updatable subscriptions, see [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 For information about permissions required by agents and best practices for replication security, see [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md) and [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## Options  
 **Snapshot Agent**  
 Displayed for all publications. Click **Security Settings** to specify security settings in the **Snapshot Agent Security** dialog box.  
  
 Click **Help** on the **Snapshot Agent Security** dialog box for more information about the permissions required for accounts used by the Snapshot Agent.  
  
 **Log Reader Agent**  
 Displayed for all transactional publications. Click **Security Settings** to specify security settings in the **Log Reader Agent Security** dialog box.  
  
 Click **Help** on the **Log Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Log Reader Agent.  
  
> [!NOTE]  
>  There is one Log Reader Agent for each database that is published using transactional replication. If a transactional publication already exists in the database, the security settings are read-only. You can change the settings in the **Publication Properties** dialog box, but changes affect all transactional publications in the database.  
  
 **Queue Reader Agent**  
 Displayed for transactional publications that allow updatable subscriptions. Click **Security Settings** to specify security settings in the **Queue Reader Agent Security** dialog box. A Queue Reader Agent job is created when this wizard completes; it does not depend on you creating any queued updating subscriptions. If you do not plan to create any queued updating subscriptions, you can disable the job. Right-click the job (named in the form: *[\<Publisher>].\<integer>*.) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **Jobs** folder, and then click **Disable**.  
  
 Click **Help** on the **Queue Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Queue Reader Agent.  
  
> [!NOTE]  
>  There is one Queue Reader Agent for each distribution database (and all Publishers that it serves). If a transactional publication that allows queued updating subscriptions already exists on any of the Publishers that use a given distribution database, the security settings are read-only. You can change the account under which the Queue Reader Agent runs and makes connections in the **Distributor Properties** dialog box, but changes affect publications at all Publishers that use the distribution database.  
  
## See Also  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Identity access and control for Replication](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [Publish Data and Database Objects](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
