# About the Core Equipment Vocabulary

This is the IEC 61970-452 core equipment profile.

![Core Equipment Main](assets/core_equipment-20240327.png)

An application supporting CGMES shall meet the following requirements and
constraints:

* Model exchange containing node-breaker, bus-branch and hybrid (mixed
  bus-branch and node-breaker) model representations;
* One model authority set containing modelling parts representing different
  granularity, i.e. different subsets of the model can be modelled in detail
  as a node-breaker model while other subsets can be with bus-branch level of
  detail;
* ConnectivityNode object instances shall be included in Core Equipment profile
  instance;
* TopologicalNode object instances are representing a given result of a
  topology processing (EXCH1, EXCH2) or a designed topology;
* The association end Terminal.ConnectivityNode is optional in the Core
  Equipment profile instance. However, a model including topology requires
  Terminals to have an association to either ConnectivityNode, TopologyNode or
  both;
* The association end ConnectivityNode.TopologicalNode is required in the
  Topology profile distribution;
* The association end Terminal.TopologicalNode is optional, while at least one
  instance of TopologicalNode.Terminal is required;
* The association end Terminal.TopologicalNode is required in cases where a
  RegulatingControl is associated with a Terminal; Justification and
  consequence:
* ConnectivityNode is a required class in Core Equipment instance data.
  Therefore, all model representations are built with ConnectivityNode-s;
  Historically there is assumption that ConnectivityNode-s are for node-breaker
  style modelling only (whereas TopologicalNode-s are for bus-branch modelling,
  typically resulting from topology processing on node-breaker models, with
  buses used to construct the admittance matrix for power flow).
  ConnectivityNode-s can actually be used for both modelling styles, which is
  the prescribed way of describing electrical connectivity of
  ConductingEquipment. For pure bus-branch models, this will mean one
  additional object (ConnectivityNode) per existing TopologicalNode.
* The header information provided in the attribute Model.profile does not give
  any information about the model authority set model representation
  (bus-branch, node-breaker or hybrid).
