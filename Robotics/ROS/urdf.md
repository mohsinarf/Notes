# URDF File (Unified Robot Description Format)

The Unified Robot Description Format (URDF) is an XML format used to describe the physical and kinematic properties of a robot. It provides a standardized way to model robots for simulation, visualization, and control.

---

## What are Links?

A **link** represents a single rigid part of a robot. If two parts of a robot can move independently of each other, they must be defined as separate links. 

### Key Points About Links:
- The **origin** of a link can be placed arbitrarily, but for rotating links, it should align with the pivot point to ensure correct motion representation.
- Links can have visual, collision, and inertial properties, each defined independently.

---

## What are Joints?

**Joints** connect links and define their relationships, such as relative position and orientation. They determine how links move with respect to one another.

### Key Points About Joints:
- Each joint connects a **parent link** to a **child link**.
- A link can have only one parent, but it can have multiple child links.
- Joints specify the type of motion between links (e.g., rotation, translation).

---

### Types of Joints

1. **Revolute**: Allows rotation within a specific range.
2. **Continuous**: Allows unlimited rotation in any direction.
3. **Prismatic**: Enables linear motion (like a sliding joint).
4. **Fixed**: The child link does not move relative to the parent link.

---

# URDF File Syntax

Below is the general structure and key elements of a URDF file.

---

## Link Syntax

### Visual Tag
Defines the appearance of the link.

- `<geometry>`: Specifies the shape, which can be a box, cylinder, sphere, or a path to a 3D mesh.
- `<origin>`: An offset for the geometry so it doesn't have to be centered at the link's origin.
- `<material>`: Defines the color or texture of the link.

### Collision Tag
Defines the physical interaction properties of the link (e.g., for detecting collisions).

- `<geometry>`: Specifies the shape, which can be a box, cylinder, sphere, or a path to a 3D mesh.
- `<origin>`: An offset for the collision geometry relative to the link's origin.

### Inertial Tag
Defines the physical mass and inertial properties of the link.

- `<mass>`: The mass of the link.
- `<origin>`: The center of mass of the link.
- `<inertia>`: The inertia matrix of the link (resistance to angular acceleration).

---

## Joint Syntax

Defines the connection between two links and the type of motion allowed.

- `<parent>`: Specifies the parent link.
- `<child>`: Specifies the child link.
- `<origin>`: The relative position and orientation of the joint.
- `<axis>`: Specifies the axis of motion (for revolute or prismatic joints).
- `<limit>`: Specifies motion limits (e.g., range of rotation or translation).

---

This structure allows URDF files to describe robots in a way that is both flexible and precise, supporting various applications like simulation and control.
