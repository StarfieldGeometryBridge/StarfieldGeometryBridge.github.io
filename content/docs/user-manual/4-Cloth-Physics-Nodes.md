---
title: "Cloth Physics Nodes"
description: ""
summary: ""
draft: false
weight: 40
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
aliases:
  - /docs/guides/cloth-physics/
  - /docs/user-manual/cloth-physics/
---


## **Nodes for Cloth Physics**
### ***Nodes for Cloth Physics: Input***
1. **Armature Input**: Allow setting an armature object for other nodes to reference. All Armature Input nodes share the same skeleton object.
    - *__Inputs__*:   
    	None
    - *__Outputs__*: 
    	hkaSkeleton: The skeleton for other node to reference. (For example, select a bone from it)

2. **Mesh Input**: Allow setting an mesh object for other nodes to reference. All Mesh Input nodes share the same mesh object.
    - *__Inputs__*: 
    	None
    
    - *__Outputs__*: 
    	Simulation Mesh: The mesh object for other node to reference. (For example, select vertices or edges from it)

### ***Nodes for Cloth Physics: Output***
1. **Graph Output**: Output node of physics data. 
    - *__Inputs__*: 
    	Physics Data: The Physics Data for output. Physics Data comes from nodes in *Category: Physics Data*.
    
    - *__Outputs__*: 
    	None

2. **Viewer Output**: Output node for visualization.
    
    - *__Inputs__*: 
    	Any: Allow any type of input. Used for visualization.
    
    - *__Outputs__*: 
    	None

### ***Nodes for Cloth Physics: Select***
1. **Mesh Attributes Selection**: Outputs a set of indices based on whether the attribute value of each element satisfies the selection condition.
    - *__Inputs__*: 
    	Mesh: The mesh object to select elements from.
    
    - *__Outputs__*: 
    	Indices On Domain: A set of selected indices on a certain Domain ("POINT", "EDGE" or "FACE").
    
    - *__Parameters__*:
    	Domain: Either "Point" or "Edge" or "Face", the type of element being selected.
    	Type: Attribute type. The type of attribute value.
    	Attribute: Attribute name.
    	Operator: Methods to compare attribute value with Operand parameter.
    	Operand: Threshold value, used together with Operator parameter.

2. **Pick Bone From Skeleton**: Outputs a bone that is selected from input skeleton
    - *__Inputs__*: 
    	Skeleton: The skeleton to choose bone from.
    
    - *__Outputs__*: 
    	Bone: The selected bone.
    
    - *__Parameters__*: 
    	Bone: The selected bone name.

3. **Match Bone Names**: Outputs a set of bones by name matching from input skeleton
    - *__Inputs__*: 
    	Skeleton: The skeleton to choose bones from.
    
    - *__Outputs__*: 
    	Bones: The selected set of bones.
    
    - *__Parameters__*: 
    	Match Mode: Method to match string with bone names.
    	Matching String: The object string for matching
    	Matched Bone Dropdown: For display. Shows which bones are selected by this node.

4. **Combine Bone Selection**: Outputs a set of bones by combining input sets of bones
    - *__Inputs__*: 
    	Bone(s) A: A bone or a set of bones.
    	Bone(s) B: The second bone or set of bones.
    
    - *__Outputs__*: 
    	Bones: The combined set of bones.

### ***Nodes for Cloth Physics: Simulation***
1. **Sim Cloth Data**: Combine input Particles and Colliders to form Simulation Cloth Data. 
    - *__Inputs__*: 
    	Particles: Constrained Particles defined in previous stage. (See [Pre-requisite Knowledge](#prerequisite-knowledge): "**Particles**" & "**Constraints**").
           Colliders: Colliders for simulation. Maximum 32 nodes from *Category: Colliders*.
    
    - *__Outputs__*: 
    	Cloth Data: Output Simulation Cloth Data. 
    
    - *__Parameters__*:
    	Gravity Vector: Gravity's direction and value. (0, 0, -9.81) is earth gravity that pointing downwards.
    	Global Damping Per Second: Simulates air viscosity or resistance. How much percentage of velocity of a particle will lose every second.

2. **Particles From Mesh**: Generate Particles at each vertex of the input mesh. (Particles are key elements in **Stage 2**)
    
    - *__Inputs__*: 
    	Mesh: The mesh to generate particles from.
    	Bind To Bone: Which bone the fixed particles will copy movements from.
    	Fixed Particle Indices: Which particles are fixed (connects to non-cloth sim areas). 
    
    - *__Outputs__*: 
    	Particles: A group of unconstrained cloth Particles.
    	
    - *__Parameters__*:
    	Particle Mass: The mass of each particle.
    	Particle Radius: How large each particle is.
    	Particle Friction: The friction factor of each particles.

3. **Links From Mesh**: Generate Links from selected edges of the input mesh. (used to define constraints in *Category: Constraints*)
    - *__Inputs__*: 
    	Mesh: The mesh to select links from.
    	Edge Indices: Selected edge indices on Domain "Edge". (Default: all edges)
   
    - *__Outputs__*: 
    	Links: A selected set of edges with stiffness value.
    
    - *__Parameters__*:
    	Link Stiffness: How strong the links are. (1 means infinitely strong and 0 means infinitely weak)

4. **Disable Collision**: Disables collision between a Collider and selected Particles.
    - *__Inputs__*: 
    	Cloth Data: Input Simulation Cloth Data to operate on.
    	Particle Indices: Selected set of vertex indices on Domain "Point".
    
    - *__Outputs__*: 
    	Cloth Data: Output Simulation Cloth Data after the operation. 
    
    - *__Parameters__*:
    	Collider: Collision between this Collider and selected particles is disabled.

5. **Set Particle Attributes**: Set Mass, Radius and Friction for selected Particles from input set of Particles.
    - *__Inputs__*: 
    	Particles: Input set of Particles to operate on.
    	Particle Indices: Selected set of vertex indices on Domain "Point".
    
    - *__Outputs__*: 
    	Particles: Output set of Particles with updated physics properties. 
    
    - *__Parameters__*:
    	Particle Mass: The mass of each particle.
    	Particle Radius: How large each particle is.
	    Particle Friction: The friction factor of each particles.

### ***Nodes for Cloth Physics: Constraints***
1. **Standard Link**: Default cloth simulation links between particles. Constraint on the length of the links to their default length.
    - *__Inputs__*: 
    	Particles: Input set of Particles to add constraint to.
    	Links: A set of links to connect Particles. (Links are from "**Links From Mesh**" node)
    
    - *__Outputs__*: 
    	Particles: Output set of Particles with this Constraint.
    
    - *__Parameters__*:
    	Show Constraint: Show Vis Mesh of this constraint.

2. **Stretch Link**: Constraint the stretchiness of links between particles. Useful for cloth with elastic properties.
    - *__Inputs__*:
    	Particles: Input set of Particles to add constraint to.
    	Links: A set of links to connect Particles. (Links are from "**Links From Mesh**" node)
    
    - *__Outputs__*: 
    	Particles: Output set of Particles with this Constraint.
    
    - *__Parameters__*:
    	Show Constraint: Show Vis Mesh of this constraint.

3. **Global Bone Plane Constraint**: Constraint Particles to a Plane that copies the rotation of the input bone.
    - *__Inputs__*: 
    	Particles: Input set of Particles to add constraint to.
    	Bone: Which Bone Axes the constraint plane is in and rotates with.
    	Particle Indices: Which Particles are constrained. The input is a selected set of vertex indices on Domain "Point".
    
    - *__Outputs__*: 
    	Particles: Output set of Particles with this Constraint.
    
    - *__Parameters__*:
    	Show Constraint: Show Vis Mesh of this constraint.
    	Plane Normal Direction: Normal direction of the constraint plane.
    	Stiffness: The strength of this constraint.

4. **Local Range Constraint**: Constraint Particles within a range of their initial positions
    - *__Inputs__*: 
    	Particles: Input set of Particles to add constraint to.
    	Particle Indices: Which Particles are constrained. The input is a selected set of vertex indices on Domain "Point". Default: all particles.
        
    - *__Outputs__*: 
    	Particles: Output set of Particles with this Constraint.
        
    - *__Parameters__*:
    	Show Constraint: Show Vis Mesh of this constraint.
    	Particle Stiffness/Base Stiffness: The strength of this constraint. (0 means not at all, 1 means infinitely strong)
    	Minimum Range: Particles within this range will move freely, but outside this range will receive a corrective force.
    	Mode "Fixed": All particles get the same constraint power no matter how far they are from the body.
    	Mode "Cascade": Particles that are close to the end of a cloth bone chain are less constrained than those are far.
    	Mode "Cascade" -> Cascade Falloff Factor: How fast the constraint power decreases as the particle gets closer to the end of the cloth bone chain. (the smaller the value, the faster the constraint power decreases)
    	Constraint Normals: Weather to take normal directions of particles into consideration.

### ***Nodes for Cloth Physics: Colliders***
1. **Capsule Collider**: A collider that has a capsule shape.
    - *__Inputs__*: 
    	Bind To Bone: The bone this collider copies movements from. (weighted to this bone)
    
    - *__Outputs__*: 
    	Collider: The collider. Which can then be fed into "**Sim Cloth Data**" node.
    
    - *__Parameters__*:
    	Start Position: Location of the starting end in Bone Axes.
    	End Position: Location of the ending end in Bone Axes.
    	Radius: The radius of the capsule shape.

2. **Tapered Capsule Collider**: A capsule Collider whose one end can be bigger or smaller than the other end.
    - *__Inputs__*: 
        Bind To Bone: The bone this collider copies movements from. (weighted to this bone)
    
    - *__Outputs__*: 
        Collider: The collider. Which can then be fed into "**Sim Cloth Data**" node.
    
    - *__Parameters__*:
        Start Position: Location of the starting end in Bone Axes.
        End Position: Location of the ending end in Bone Axes.
        Start Radius: The radius of the capsule shape at the starting position.
        End Radius: The radius of the capsule shape at the ending position.

### ***Nodes for Cloth Physics: Physics Data***
1. **Two State Physics Data**: Combine Simulation Cloth Data, Simulation Mesh and Physics Bones (from *Category: Physics Bones*) to make Physics Data for graph output.
    - *__Inputs__*: 
		Cloth Data: The Simulation Cloth Data after **Stage 3**.
        Simulation Mesh: The mesh object used throughout the graph.
        Physics Bones: A set of Physics Bones defined by Driver nodes in *Category: Physics Bones*.
        
    - *__Outputs__*: 
        Physics Data: The composed Physics Data for output.

### ***Nodes for Cloth Physics: Physics Bones***
1. **Simple Triangle Bone Driver**: Drive Cloth Bones with the closest triangle from simulation to create physics visual effects. __Physics Bones are Cloth Bones **driven** by simulation.__
    - *__Inputs__*: 
        Bones: Input Cloth Bones to be driven.
        Simulation Mesh: Underlying mesh.
    
    - *__Outputs__*: 
        Physics Bone: Output Physics Bones. Physics Bones are Cloth Bones **driven** by simulation.
    
    - *__Parameters__*
        Mode: The method to pick closest triangle from a cloth bone. Both methods work similarly.