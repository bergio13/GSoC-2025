# GSoC 2025 - Integrating Agents.jl with Reinforcement Learning Techniques
## Google Summer of Code 2025 - Project Summary

This report summarizes my work for the **Google Summer of Code (GSoC) 2025** program, where I focused on integrating reinforcement learning (RL) capabilities into the [Agents.jl](https://github.com/JuliaDynamics/Agents.jl) library. **Agents.jl** is a popular and high-performance Julia library for developing agent-based models (ABMs). The primary goal of this project was to enable agents within these models to learn and adapt their behaviors using RL techniques, addressing a long-standing need identified in an old issue on the project's GitHub page ([issue 648](https://github.com/JuliaDynamics/Agents.jl/issues/648)). The first approach considered was a centralized RL model, where a single controller would manage all agents. This was quickly discarded because the action space for such a system grows exponentially with the number of agents, making it computationally infeasible.

Instead, I opted for a more scalable, decentralized approach where each agent learns based on its local neighborhood. To simplify the process and improve efficiency, I allowed agents of the same type to share a single neural network.

### Technical Implementation
The initial implementation involved creating a separate interface for adding RL training on top of a standard ABM. However, this approach made it difficult to seamlessly visualize and simulate the models with trained policies. This led to a more integrated and user-friendly solution: the creation of a new ABM type called `ReinforcementLearningABM`. This new type allows users to train, step, and plot their models with trained policies using the same familiar commands as other ABM types, streamlining the workflow.

To demonstrate the functionality, I recreated classic ABM examples inspired by the Python library for agent-based models Mesa. These included the Boltzmann money model and the Wolf-Sheep Predation model. The Boltzmann model was chosen to serve as the main tutorial for the new ReinforcementLearningABM type, providing a clear guide for new users.

The results clearly show the impact of the learned policies. You can see the distinct difference between agents moving randomly and agents using a learned policy in the videos below.

**Agents Moving Randomly:**

https://private-user-images.githubusercontent.com/68152031/481182466-fdf445a8-d833-46f8-a050-fa6bb48e7d8b.mp4?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTYzMzM5NjUsIm5iZiI6MTc1NjMzMzY2NSwicGF0aCI6Ii82ODE1MjAzMS80ODExODI0NjYtZmRmNDQ1YTgtZDgzMy00NmY4LWEwNTAtZmE2YmI0OGU3ZDhiLm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MjclMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODI3VDIyMjc0NVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTRhNzk4MjgwZmVkZDkwZjUyODE4ZWEyZjNlYjYwYWI3YTgwMTNmMmY2YWE1ZDkyMzUyNWM5Mzk2MDVjZmNhMjUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.naLn6O9qhz6ZfYr7cRcHlAJXB2GvV_crgKsFjemxRZk

**Agents with Learned Policies:**

https://private-user-images.githubusercontent.com/68152031/481182475-c5bef9f9-aef0-4f22-b323-0475faae819a.mp4?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTYzMzM5NjUsIm5iZiI6MTc1NjMzMzY2NSwicGF0aCI6Ii82ODE1MjAzMS80ODExODI0NzUtYzViZWY5ZjktYWVmMC00ZjIyLWIzMjMtMDQ3NWZhYWU4MTlhLm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MjclMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODI3VDIyMjc0NVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWI2ZjFhMTBlYzE3NWU0NmJmZWNjNTI1NGJkZWIwOTQzOThmZDQ4NmU0YTBmMjMwNGEzNTAzMDRmOTMxNWU3NjImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.cijqpm_-lPgtHrmyww_o4HbHAydh0QTPJ5U-72rz_YE

### Deliverables and Contributions
- Core Feature: Implemented the `ReinforcementLearningABM` type to seamlessly integrate RL training into agent-based models.
- Examples and Tutorials: Developed a detailed tutorial using the Boltzmann model to guide users on how to apply RL techniques within the new framework.
- Code: All code contributions are available in this [pull request](https://github.com/JuliaDynamics/Agents.jl/pull/1170)


## Links
- Pull Request - https://github.com/JuliaDynamics/Agents.jl/pull/1170
- MARL - https://www.marl-book.com/
- Agents.jl - https://github.com/JuliaDynamics/Agents.jl
- Mesa RL - https://github.com/projectmesa/mesa-examples/tree/main/rl

