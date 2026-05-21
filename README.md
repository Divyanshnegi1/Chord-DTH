# Chord-DHT-graphi-viz
An implementation of chord protocol based distributed hash table for scalable peer to peer networks
Chord DHT Network Graph Visualization
A comprehensive implementation of the Chord Distributed Hash Table (DHT) protocol with advanced graph visualization, monitoring, and management capabilities.

🚀 Features
Complete Chord DHT Implementation: Full Chord protocol with finger tables, stabilization, and fault tolerance
Interactive Network Visualization: Real-time SVG/PNG graph generation showing network topology
Advanced Monitoring: Prometheus metrics integration for network health and performance tracking
Rich Terminal Interface: Beautiful terminal UI with progress bars, tables, and interactive menus
Data Encryption: Built-in cryptographic security for stored data
Network Backup & Recovery: Automatic backup system with state restoration capabilities
Load Balancing: Dynamic load redistribution across network nodes
Health Monitoring: Comprehensive network health checks and diagnostics
📋 Requirements
Python 3.7+
Graphviz (for graph visualization)
System Dependencies
Ubuntu/Debian:

sudo apt-get update
sudo apt-get install graphviz graphviz-dev
macOS:

brew install graphviz
Windows: Download and install Graphviz from the official website.

🛠️ Installation
Clone the repository:
git clone https://github.com/kagdiyal04/Chord-DHT-graphi-viz.git
cd Chord-DHT-graphi-viz
Install Python dependencies:
pip install -r requirements.txt
Verify installation:
python Main.py --help
🎯 Quick Start
Basic Usage
# Start interactive mode
python Main.py

# Start with specific parameters
python Main.py --m 5 --nodes 10 --data 20
Command Line Arguments
--m: Ring size parameter (1-32, determines max nodes = 2^m)
--nodes: Initial number of nodes to create
--data: Amount of test data to generate
Interactive Operations
Once running, you can perform various operations:

Insert new node - Add nodes to the network
Find data - Search for stored data
Insert data - Store new data in the network
Print network graph - Generate visual representation
Print network info - Display network statistics
Delete node - Remove nodes from the network
Show metrics - View performance metrics
Backup network - Create network state backup
Load balancing - Redistribute network load
Network health check - Verify network integrity
Show all network data - Display all stored data
📊 Network Visualization
The system generates comprehensive network visualizations showing:

Node Connections: Successor and predecessor relationships
Finger Tables: All finger table entries for optimal routing
Data Distribution: Visual representation of data storage across nodes
Network Topology: Complete network structure
Example visualization files:

network_graph.svg - Scalable vector graphics (recommended)
network_graph.png - Raster image format
🔧 Configuration
Environment Variables
# Optional: Set custom log level
export CHORD_LOG_LEVEL=INFO

# Optional: Set custom metrics port
export CHORD_METRICS_PORT=8000
Network Parameters
m parameter: Controls ring size (2^m possible positions)
Small networks: m=3-5 (8-32 positions)
Medium networks: m=8-12 (256-4096 positions)
Large networks: m=16-20 (65536-1048576 positions)
📈 Monitoring
Prometheus Metrics
The application exposes metrics on port 8000 by default:

curl http://localhost:8000/metrics
Available metrics:

chord_total_nodes - Total nodes in network
chord_total_data - Total data items stored
chord_operations_total - Network operations counter
chord_latency - Operation latency
chord_load - Network load distribution
chord_node_health - Healthy node count
Health Checks
Regular health monitoring includes:

Node responsiveness
Data consistency verification
Load balance assessment
Backup integrity checks
Finger table accuracy
🔐 Security Features
Data Encryption: All stored data is encrypted using Fernet symmetric encryption
Authentication Tokens: Node-level authentication for operations
Secure Communication: Encrypted data transfer between nodes
Backup Security: Encrypted backup files with integrity verification
🏗️ Architecture
Core Components
Node.py: Individual Chord node implementation

Finger table management
Data storage and encryption
Routing and lookup algorithms
Backup and recovery mechanisms
Network.py: Network-wide operations and management

Node lifecycle management
Global monitoring and metrics
Load balancing and health checks
Backup coordination
Main.py: User interface and application entry point

Interactive terminal interface
Command-line argument processing
Visualization coordination
Application lifecycle management
Key Algorithms
Consistent Hashing: SHA-1 based key distribution
Finger Table Routing: Logarithmic lookup performance O(log N)
Stabilization Protocol: Maintains network integrity during changes
Load Balancing: Dynamic redistribution for optimal performance
🔄 Backup & Recovery
Automatic Backups
Periodic network state snapshots
Node-level data replication
Configurable backup intervals
Encrypted backup storage
Manual Backup
# Through interactive menu option 8
# Or programmatically:
network.backup_network_state()
Recovery
# Restore from backup file
network.restore_from_backup('network_backup_1234567890.json')
🧪 Examples
Programmatic Usage
from Node import Node
from Network import Network

# Create network
Node.m = 5  # Ring size = 2^5 = 32
node_ids = [0, 10, 20, 30]
network = Network(5, node_ids)

# Add nodes
for node_id in [5, 15, 25]:
    network.insert_node(node_id)

# Store data
network.insert_data("example_file.txt")

# Find data
result = network.find_data("example_file.txt")
print(f"Found: {result}")

# Generate visualization
network.print_network()
Performance Testing
import time
from random import choice

# Measure lookup performance
start_time = time.time()
for i in range(1000):
    key = f"test_file_{i}.txt"
    network.insert_data(key)
    
lookup_time = time.time() - start_time
print(f"Average lookup time: {lookup_time/1000:.4f} seconds")
🐛 Troubleshooting
Common Issues
ImportError: No module named 'pydotplus'

pip install pydotplus
Graphviz not found

Install system Graphviz package
Ensure it's in your PATH
Permission denied for port 8000

# Use different port
export CHORD_METRICS_PORT=8080
Large network visualization slow

Use SVG format for better performance
Consider reducing node count for visualization
Debug Mode
# Enable verbose logging
python Main.py --m 3 --nodes 5 --data 10 2>&1 | tee debug.log
🤝 Contributing
Fork the repository
Create a feature branch (git checkout -b feature/amazing-feature)
Commit your changes (git commit -m 'Add amazing feature')
Push to the branch (git push origin feature/amazing-feature)
Open a Pull Request
Development Setup
# Install development dependencies
pip install pytest pytest-cov black flake8 mypy

# Run tests
pytest tests/

# Format code
black *.py

# Lint code
flake8 *.py
📝 License
This project is licensed under the MIT License - see the LICENSE file for details.

🙏 Acknowledgments
Team Glitch - Original development team
Chord DHT Protocol - Ion Stoica, Robert Morris, David Karger, M. Frans Kaashoek, Hari Balakrishnan
Graphviz - Graph visualization software
Rich Library - Beautiful terminal interfaces
📚 References
Chord: A Scalable Peer-to-peer Lookup Service for Internet Applications
Distributed Hash Tables
Consistent Hashing
📊 Performance Characteristics
Operation	Time Complexity	Space Complexity
Lookup	O(log N)	O(log N)
Insert	O(log N)	O(1)
Delete	O(log N)	O(1)
Join	O(log² N)	O(log N)
Leave	O(log² N)	O(1)
Where N is the number of nodes in the network.
