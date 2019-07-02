TMDSP Instances
========================

These are instances of the Time- and Machine-Dependent Scheduling Problem
(TMDSP). In this problem, jobs, machine utilization, and production rates vary
according to the time. In each period, a given job can be executed in a subset
of machines with different capacities and productions rates. The objective is
to deploy a feasible schedule with the minimum total completion time. For more
details, see
[this paper](https://ceandrade.github.io/publication/andrade-2019-scheduling-fota)

> C.E. Andrade, S.D. Byers, V. Gopalakrishnan, E. Halepovic, D.J. Poole,
> L.K. Tran, C.T. Volinsky. Scheduling software updates for connected cars
> with limited availability. Applied Soft Computing 82 (2019) 105575,
> DOI [10.1016/j.asoc.2019.105575](http://dx.doi.org/10.1016/j.asoc.2019.105575)


We have 3 groups of instances:

- Synthetic: 60 files, total of 1 MB;

- Common jobs: 71 files, total of 1.1GB;

- Rare jobs: 82 files, total of 1.1GB.

Note that the `common ` and `rare` subsets are large real-world instances, with
interest by the industry. While `synthetic` set can be used to test-proof your
strategy, we recommend testing all large instances for meaningful value of your
code.

These instances are release under modified BSD license. When using these
instances or derivative works, you must cite the above paper (Andrade et al.,
2019). Please, refer to LICENSE.md for more details.


Format
----------------------

Following, we have an example of the file format. All lines starting with "#"
should be considered commnetaries and should be ignored. The general format of
this file consists in a tag marking a beginning of a section. Each tag appears
alone in the line. The following lines contains the data correspondent to that
tag. This is an example:

```
###############################################################################
# (c) Copyright 2019
#     AT&T Labs Research.
#     All Rights Reserved.
#
# All information in this file does neither reflect nor imply an actual
# business case for AT&T, and/or associated companies. They are generalized
# data used to assess performance of the algorithms only.
#
# See LICENSE.md file for license information.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
# AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
# ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE
# LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
# CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
# SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
# CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
# ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
# POSSIBILITY OF SUCH DAMAGE.
###############################################################################

###############################################################################
# Number of periods
###############################################################################

periods
6

###############################################################################
# Number of machines
###############################################################################

machines
3

###############################################################################
# Capacity of each machine in each period (per line). We consider that the 
# machines and periods are indexed from 0 using natural numbers, and the 
# capacities are floating point numbers in machine utilization units (muu).
# Note that a machine may have no entry for all periods.
# Format: machine_id period utilization_rate capacity
###############################################################################

machine_periods
0 0 1.0 10.0
0 1 1.0 10.0
0 2 1.0 15.0
0 3 1.0 15.0

1 0 1.0 15.0
1 2 1.0 30.0

2 1 1.0 25.0
2 2 1.0 25.0
2 5 1.0 20.0

###############################################################################
# Number of jobs
###############################################################################

jobs
4

###############################################################################
# Load or demand of each job given in floating point numbers in production
# units (pu).
###############################################################################

loads
15.0 15.0 20.0 50.0

###############################################################################
# Maximum consumption of each job in each period (per line). We consider that 
# the jobs, machines, and periods are indexed from 0 using natural numbers, 
# and the consumptions are floating point numbers in machine utilization
# units (muu). Note that a job may have no entry for all periods and machines.
# Format: job_id period machine_id maximum_consumption
###############################################################################

jobs_periods
0 0 0 5.0
0 2 0 10.0
0 1 2 5.0

1 4 0 15.0
1 0 1 10.0
1 2 1 15.0

2 4 1 10.0
2 2 1 10.0

3 4 0 15.0
3 2 1 5.0
3 5 2 5.0
3 7 2 15.0

###############################################################################
# Global capacity given by a floating point number in production units (pu).
###############################################################################

global_capacity
50.0

###############################################################################
# Maximum number of jobs per period given by an integer number.
###############################################################################
maximum_num_jobs_per_period
10

###############################################################################
# Minimum amount that a job must consume when scheduled in one given machine 
# and period. Given by a floating point number in machine utilization
# units (muu).
###############################################################################

minimum_load
0.0
```

