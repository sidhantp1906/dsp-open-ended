# Import packages
import biosppy
import pyhrv.tools as tools
from pyhrv.hrv import hrv
from opensignalsreader import OpenSignalsReader

# Load sample ECG signal stored in an OpenSignals file
signal = OpenSignalsReader('SampleECG.txt').signal('ECG')


# Get R-peaks series using biosppy
rpeaks = biosppy.signals.ecg.ecg(signal)[2]

# Compute NNI series
nni = tools.nn_intervals(rpeaks)


# OPTION 1: Compute Time Domain parameters using the ECG signal
signal_results = hrv(signal=signal)

# OPTION 2: Compute Time Domain parameters using the R-peak series
rpeaks_results = hrv(rpeaks=rpeaks)

# OPTION 3: Compute Time Domain parameters using the NNI-series
nni_results = hrv(nni=nni)
# Print SDNN
print(signal_results['sdnn'])


# Print RMSSD
print(signal_results['rmssd'])
# Define custom input parameters using the kwargs dictionaries
kwargs_time = {'threshold': 35}
kwargs_nonlinear = {'vectors': False}
kwargs_welch = {'nfft': 2**8}
kwargs_lomb = {'nfft': 2**16}
kwargs_ar = {'nfft': 2**8}
kwargs_tachogram = {'hr': False}
kwargs_ecg_plot = {'title': 'My ECG Signal'}

# Compute HRV parameters
hrv(nni=nni, kwargs_time=kwargs_time, kwargs_nonlinear=kwargs_nonlinear, kwargs_ar=kwargs_ar,
   kwargs_lomb=kwargs_lomb, kwargs_welch=kwargs_welch, kwargs_tachogram=kwargs_tachogram)
# Define custom input parameters using the kwargs dictionaries
kwargs_time = {
   'threshold': 35,     # Valid key, will be used
   'nfft': 2**8         # Invalid key for the time domain, will be ignored
}

# Compute HRV parameters
hrv(nni=nni, kwargs_time=kwargs_time)
