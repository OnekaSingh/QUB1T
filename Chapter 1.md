1: Atoms of Computation

  from qiskit.circuit import QuantumCircuit
  from qiskit_aer import AerSimulator
  from qiskit.visualization import plot_histogram
  from qiskit.primitives import Sampler, Estimator, BackendEstimator, BackendSampler
  
  qcirc = QuantumCircuit(8)
  qcirc.measure_all()
  qcirc.draw()
  
  backend = AerSimulator() #chooses the backend
  sampler = BackendSampler(backend) #create a sampler object
  sampler2 = Sampler()
  result = sampler.run(qcirc).result() #runs circuit and saves results
  print("Counts", result.quasi_dists[0]) #how many times a shot was measured
  plot_histogram(result.quasi_dists[0]) #plots the result probability
