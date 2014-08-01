.. Licensed to the Apache Software Foundation (ASF) under one
   or more contributor license agreements.  See the NOTICE file
   distributed with this work for additional information#
   regarding copyright ownership.  The ASF licenses this file
   to you under the Apache License, Version 2.0 (the
   "License"); you may not use this file except in compliance
   with the License.  You may obtain a copy of the License at
   http://www.apache.org/licenses/LICENSE-2.0
   Unless required by applicable law or agreed to in writing,
   software distributed under the License is distributed on an
   "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
   KIND, either express or implied.  See the License for the
   specific language governing permissions and limitations
   under the License.
   

What's New in |version|
=======================

CloudStack |version| 包括以下新的特性和改进.

.. contents::
   :local:
   :backlinks: top


支持管理 root disks存储
--------------------------------------

   使用Root disks主存储插件. 参考 `Configuring a Storage Plug-in 
   <http://docs.cloudstack.apache.org/projects/cloudstack-installation/en/master/configuration.html#configuring-a-storage-plug-in>`_
      
   ====================== ============================================================================
   支持的hypervisors: XenServer, VMware
   ====================== ============================================================================


Root disk 大小重置
----------------

   当对同一个操作系统的摸板，根据系统盘大小不同设置多个摸板时，允许重置系统大小
   
   ====================== ============================================================================
   支持的hypervisor:       KVM
   Link                   `Root resize Functional spec`_
   ====================== ============================================================================


每一个主存储的超分使用
------------------------------------

    在全局配置参数中为每一个主存储添加配置参数``storage.overprovisioning.factor``.
   
   -  admin can update an existing primary store by setting 
      ``storage.overprovisioning.factor`` in the per primary setting.
   
   -  This value will override the value at the global level. This leverages 
      the granularity of global parameters introduced in 4.2
   
   -  如果要使默认的全局配置参数, 将该值设置为空.
   
   -  若要禁用超分使用，将该设置为1.
 
   ====================== ============================================================================
   支持的hypervisor:       KVM
   link                   `Storage Over Prov. Functional spec`_
   ====================== ============================================================================


支持VMWare  DRS
----------------------

   VMware DRS(分布式资源调), VM HA(高可用): 
   Provide highly available resources to your workloads. Balance workloads for 
   optimal performance. Scale and manage computing resources without service 
   disruption.
   
   -  **Load Balancing**: distribution and usage of CPU and memory resources 
      for all hosts and VMs in the cluster are continuously monitored and 
      compared to ideal resource utilization given the attributes of the 
      cluster’s resource pools and VMs, the current demand, and the imbalance 
      target. It then performs (or recommends) virtual machine migrations 
      accordingly. Also, when a VM is powered on in the cluster, DRS attempts 
      to maintain proper load balancing by either placing the VM on an 
      appropriate host or making a recommendation.
   
   -  **Power Management**: When the vSphere Distributed Power Management 
      (DPM) feature is enabled, DRS compares cluster- and host-level capacity 
      to the demands of the cluster’s VMs, including recent historical demand. 
      It places (or recommends placing) hosts in standby  power mode if 
      sufficient excess capacity is found or powering on hosts if capacity is 
      needed. Depending on the resulting host power state  recommendations, 
      VMs might need to be migrated to and from the hosts as well.
   
   -  **Affinity Rules**: control the placement of virtual machines on hosts 
      within a cluster, by assigning affinity rules 
   
   ====================== ============================================================================
   支持的 hypervisors: VMware
   Link                   `DRS functional spec`_
   ====================== ============================================================================


Region 级别 Guest networks and VPC 
----------------------------------

   创建Region 级别的 Guest networks 和 VPC . Allowing VPC tiers and guest网络accessibility across zones.

   ====================== ============================================================================
   支持 hypervisors:         N/A
   Link                   `VPC region functional spec`_
   ====================== ============================================================================


Virtual Router Service Failure Alerting
---------------------------------------

   Send failure alerts to management server to notify admins using `Monitoring
   VR services <https://cwiki.apache.org/confluence/display/CLOUDSTACK/Monitoring+VR+services>`_
   introduced in CloudStack 4.3.

   ====================== ============================================================================
   Supported hypervisors: xenserver, kvm, vmware
   Link                   `VR failure alerting functional spec`_
   ====================== ============================================================================


 通过 OVS插件，实现分布式路由network ACL
----------------------------------------------------

   通过 OVS插件，实现分布式路由network ACL.

   ====================== ============================================================================
   支持的 hypervisors:      xenserver, kvm, vmware
   Link                   `CLOUDSTACK-6161 <https://issues.apache.org/jira/browse/CLOUDSTACK-6161>`_
   ====================== ============================================================================


Hyper-V support 改进
----------------------------

Zone Wide Primary Store in Hyper-V
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

   使用共享SMB 为 zone 提供主存储.

   ====================== ============================================================================
   Supported hypervisors: Hyper-V
   Link                   `Hyper-V zone wide storage functional spec`_
   ====================== ============================================================================


在Hyper-V上支持VPC
~~~~~~~~~~~~~~~~~~~~~~

   基于Hyper-V提供 VPC capability .
   
   ====================== ============================================================================
   Supported hypervisors: Hyper-V
   Link                   `VPC support on Hyper-V functional spec`_
   ====================== ============================================================================


支持为Hyper-V的存储提供在线迁移
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

   Hyper-V 2012 R2 allows migration of volumes (virtual disks) of a virtual
   machine from one storage to another, while the virtual machine continues to
   run. It also allows live migration of a virtual machine and its volumes to
   another host and storage without any downtime.

   The intend of this feature is to enable support of live migration of a
   virtual machines with its volumes across hosts and storage pools. It'll
   also migration of volumes across storage pools while the volume stays
   attached to a running virtual machine.

   ====================== ============================================================================
   Supported hypervisors: Hyper-V
   Link                   `Hyper-V storage motion functional spec`_
   ====================== ============================================================================


.. _Hyper-V storage motion functional spec: https://cwiki.apache.org/confluence/display/CLOUDSTACK/Storage+motion+for+Hyper-V
.. _Hyper-V zone wide storage functional spec: https://cwiki.apache.org/confluence/display/CLOUDSTACK/Zone+wide+primary+storage+for+Hyper-V
.. _VPC support on Hyper-V functional spec: https://cwiki.apache.org/confluence/display/CLOUDSTACK/VPC+support+on+Hyper-V
.. _VR failure alerting functional spec: https://cwiki.apache.org/confluence/display/CLOUDSTACK/Virtual+Router+Service+Failure+Alerting
.. _VPC region Functional spec: https://cwiki.apache.org/confluence/display/CLOUDSTACK/Region+level+VPC+and+guest+network+spanning+multiple+zones
.. _Storage Over Prov. Functional spec: https://cwiki.apache.org/confluence/display/CLOUDSTACK/Storage+OverProvisioning+as+Per+Primary+Basis
.. _Root resize functional spec: https://cwiki.apache.org/confluence/display/CLOUDSTACK/Root+Resize+Support
.. _DRS functional spec: https://cwiki.apache.org/confluence/display/CLOUDSTACK/VMWare+Enhancements+-+Support+for+DRS+and+VM+HA
